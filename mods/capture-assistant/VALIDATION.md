# Validation — 0.1.1

Tested against upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`, LuaJIT, and locally imported FireRed and LeafGreen data. No player saves were loaded.

The shared assistant suite passes **140 checks per edition (280 total)**. These include:

- Every supported healing item preview compared with native field application, including sleep/numeric status, revival and Full Restore.
- Exact inventory consumption, no preview mutation or RNG consumption, scarce stock, eggs, premium protection, one-Pokémon targeting and status/revival preferences.
- Stale party/inventory/identity rejection, single-use confirmation, busy-state refusal and stopping a partially completed batch when an item handler refuses.
- Catch probability vectors and the actual native four-roll acceptance/rejection boundary; Net, Dive and Timer bonuses; lower-HP/sleep scenarios; Master Ball protection, no stock and excluded battle types.
- Capture browsing leaves session, battle and RNG unchanged; catch-rate hook warnings and selected moveset hazards.
- Menu navigation, cancel-default review, settings, close/back controls and session invalidation.
- Actual production Loader/sandbox loading of both packages with an in-memory filesystem, START registration, native settings update/write path, L/R help lease restoration and confirmed healing.
- Battle input/update wrappers suppress underlying calls while the assistant is open and consume closing input; SELECT passthrough, native modal ownership and option-disable/re-enable cleanup.

Manifest validation, ROM-content lint and Gen III static compatibility checks pass for both packages. The static checker reports unresolved dynamic calls; production-loader checks exercise their concrete paths. Logs are in `tools/party-assistants/results` in the source repository.

Native UI images were rendered from actual imported font/frame draw traces and visually inspected. They use synthetic sessions and do not prove live device input/display behaviour.

## Dual Screen handoff — 0.1.1

The full collection-loader suite passes **342 checks per edition**, including 30 new handoff checks per edition. These verify R entry, exact screen ownership, native battle drawing above, panel drawing once below, touch comparison/risk navigation and Back, no queued battle action, unchanged save state, no live detachment, display disable/re-enable fallback, old-package protocol refusal and stale-loader rejection.

The actual companion renderer was GPU-rendered with a synthetic encounter and visually inspected (`docs/screenshots/capture-assistant/dual-screen.png`). Physical dual-screen hardware was not tested for this change.

Run `mods/frlg_dual_screen/tests/collection_test.lua` from the host checkout with `FRLG_COLLECTION_PATH`, `KANTO_GEAR_MOD_PATH`, `POKEPORT_VERSION` and `POKEPORT_GBA_CACHE` set. The capture preview harness is `tools/frlg-dual-screen/capture_preview`.

## Reproduce

From the collection root:

```sh
python3 tools/party-assistants/check.py --host /path/to/gen1recomp --lua /path/to/luajit --cache-root /path/to/imports
```

The cache root contains `firered/data/generated/gba` and `leafgreen/data/generated/gba`. The checker uses synthetic sessions only. Its filesystem for loader persistence is in memory.

To render the UI, run `tools/party-assistants/capture.lua` from the host checkout with LuaJIT. Arguments are the collection root, edition, edition's GBA cache directory and a scratch trace directory. Then run `tools/render-manager-traces.py` on that scratch directory using Python with Pillow. Never distribute the imported cache or raw trace paths.

## Limits

No full live gameplay run or physical controller/Android test was performed. Battle lifecycle tests isolate native methods with call counters; native catch calculations and field item effects are tested directly. The explicit Dual Screen handoff is covered by loader/renderer tests but has not been device-tested. Arbitrary other mods and every engine revision in the manifest range are not covered.
