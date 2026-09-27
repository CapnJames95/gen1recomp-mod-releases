# Validation — 27 September 2026

Host source: `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf` (official dev).
Base: AverageConsumer/kanto-gear `6155d4d9c01f9b2fe44840382193ef3ad1db332c` (3.3.3).
LuaJIT for behavioral checks; LÖVE 11.5 for GPU previews. Plain Lua 5.4 is not a supported runner for the inherited main chunk.

## 0.3.13 — Inline summary IVs

The collection suite loads Summary IVs alongside existing mods, verifies the native Skills fallback and six IV rows, and checks that disabling the mod restores the companion adapter. Summary IVs also has 46 native-data checks per edition. Native summary render traces were visually inspected; this addition has not been physically tested on Android/Thor.

## Results

All **16 selected suites passed**, eight for each edition:

| Suite | FireRed | LeafGreen | Scope |
| --- | ---: | ---: | --- |
| Native data | 1,424 | 1,426 | Species, native read model, sparse storage, inventory, 425 maps and edition-specific encounters |
| Pointer bridge | 22 | 22 | Captured contacts, native forwarding, cancellation, wrapper release and native pointer-hook compatibility |
| Runtime | 949 | 949 | Actual loader/manifest, menus, ownership, summaries, native battle choices and save identity |
| Controls | 1,395 | 1,395 | Real native UI handlers, PC/naming/quantity/confirmation paths |
| Route progress | 42,806 | 42,806 | Flags, objectives, item radar; includes 40,443 radar positions per edition |
| Online compatibility | 1,046 | 1,046 | Offline fixtures for link admission/fingerprint and native link UI ownership; no live network session |
| Collection integration | 312 | 312 | All current collection mods loaded, all ten mod menu entries, lower-only draw dispatch, retained modal stack, 25 live toggles, native persistence dispatch, removed strip hitboxes preserve physical input, native fallback, direct row taps, detached editor update forwarding and hotkey debouncing, native Gen3 touch/mouse callback dispatch, removed Controls shortcut, all ten Home shortcuts, disabled/uninstalled visibility and safe launch, Start-menu filtering and restoration when the companion is disabled |
| Targeted encounters | 6,821 | 6,833 | Native table enumeration, level bands, caught/seen/new, fresh eligibility, stale-map rejection, busy guards, real battle transition and selected species generation |

Some suites rerun the native-data setup; these counts must not be summed as independent coverage. Data comes from the user's previously imported caches. Sessions are freshly generated fixtures, never their player save.

- Strict modkit fixture validation: passed, zero findings.
- Content lint: passed, zero findings.
- Gen3 static scan: zero errors, six warnings. Five compare the strings `gold`/`silver` in non-version contexts (stamp tiers/battle colors); one concerns the retained legacy Bag backend after the native path. The actual Gen3 runtime/control suites exercise the native path. The raw report is retained in `tools/frlg-dual-screen/results/frlg_dual_screen-gen3check.json`.
- Actual GPU renderers produced 30 native companion views (15 light, 15 dark) and eight collection/encounter views, plus Home pages 2/3 with the ten mods enabled and page 3 disabled. Visually inspected. Virtual control buttons and their Home shortcut were removed in 0.2.2.
- Encounter Tour 0.1.2 includes the 0.1.1 fix replacing its prohibited Gen2 Permissions import with the shared CollPermissions module. Its native FireRed engine test passed, including landing checks, Zapdos interaction and START-before-tour pause. Both-edition collection tests load the corrected package.

- Shiny Hunter 0.1.4 also passed its native FireRed engine regression suite, including real Loader/Storage/Input/FixedStep integration and reset/capture protections.

- Battery icon/percentage header previews were rendered with a simulated 57% reading. Tap/release, duplicate tap suppression, drag-away cancellation, toggling back and unavailable-reading formatting were smoke-checked.

- Kanto Gear 3.3.3 integration: actual raw Gen3 mouse/touch handlers open Party/Stats in stacked, side and overlay layouts. Battery toggling both ways and drag cancellation pass through those same handlers (18 additional assertions per runtime invocation). The retained Gen1/Gen2 summary regression source is outside this FRLG-only validation target.

## Not verified

The maintainer confirms AYN Thor as the only tested dual-screen device. Other dual-screen devices have not been tested. The automated suites here do not establish exhaustive coverage of display selection, touchscreen timing, unplug/reconnect, long gameplay sessions, every menu/story state, arbitrary third-party mods, later host changes or sustained GPU/readback performance. The Android multitouch patch passes `git apply --check` against the pinned source but has not been compiled or device-tested. No Android SDK or attached ADB device is available here. The virtual control deck has been removed; its historical Android multitouch patch is no longer enabled.

Five collection editors support explicit live ownership; jobs/text entry/automation regain modal ownership. Unknown native Stack panels remain modal and use a bottom-screen native-render fallback. Direct row hit tests are defined for the collection's list layouts and LegalMon keyboard, not arbitrary third-party screens. DS feature parity is intentionally excluded. Wild encounter selection uses native random encounter tables, not roaming or scripted encounters; Rock Smash uses Route scope.

## Reproduce

From the collection root, with your own imported FRLG caches and a LuaJIT binary:

```sh
python3 tools/frlg-dual-screen/check.py \
  --host "$UPSTREAM" --lua "$LUAJIT" --cache-root "$IMPORTED_GAMES"
```

`IMPORTED_GAMES` contains `firered/data/generated/gba` and `leafgreen/data/generated/gba`. Logs and a machine-readable summary are written to `tools/frlg-dual-screen/results/`.

For GPU captures, run the LÖVE app folders `tools/frlg-dual-screen/gen3_ui_preview` and `tools/frlg-dual-screen/collection_preview`. Set `KANTO_GEAR_HOST_PATH`, `KANTO_GEAR_MOD_PATH`, `KANTO_GEAR_PREVIEW_OUTPUT`, `POKEPORT_VERSION`, `POKEPORT_GBA_CACHE`, and (for collection) `FRLG_COLLECTION_PATH`. The retained KANTO variable names come from the upstream harness. Output paths must be absolute. These harnesses create isolated test sessions and render offscreen.

Package with the upstream modkit `pack` command. ZIPs contain source, documentation and licensed font assets; no ROM, save or imported game cache.

Battle tools: both-edition tests cover Y/default and custom binding dispatch, picker ownership, current-binding hints, keyboard fallback, trainer suppression, explicit throw confirmation and native inventory consumption. Native type-chart tests cover 4x, quarter resistance, immunity and status moves; quarter-badge formatting is checked. GPU previews render the command screen, all four move rows and the picker using synthetic native battle state.

Version 0.3.7 replaces the external ball-picker integration with `battle_balls.lua`. Both-edition collection tests verify own Y/custom bindings, hint updates, touch selection/confirmation, drag cancellation, focus cleanup, trainer/double guards and native inventory ownership with the other mod disabled. A separate FireRed run omits Ball Shortcut entirely: **311/311 passed**. GPU preview shows the integrated themed picker and confirmation. No physical Thor test was performed.

Version 0.3.8: FireRed and LeafGreen GPU preview runs each passed 312 collection checks. Visually checked native Poké, Great, Ultra and Timer Ball artwork in the list and Great Ball artwork on confirmation. Rendering uses item IDs through the host BagChrome API.

Version 0.3.10: inspected GPU startup previews in light/dark themes; the capture run passed all 312 collection checks. Updated classic/modern startup text and the Home/settings labels as well.

Version 0.3.11: GPU-rendered and inspected 0%, 57%, 100% and --% inside their header cell in light and dark themes. The capture run passed 312 collection checks; percentage tap behaviour is unchanged.

## 0.3.12 — Capture Assistant handoff

Both-edition collection-loader runs pass **342 checks each**, including 30 new Capture Assistant handoff checks per edition. Verified main-screen battle passthrough, single bottom-panel draw, touch row/Back input, modal ownership, no battle-command leakage or save mutation, disabled/missing-display fallback, old-version refusal and stale-loader guards. A real GPU companion preview was visually inspected. No physical device test was performed for this change. Tests live in `tests/capture_assistant_cases.lua`; preview harness: `tools/frlg-dual-screen/capture_preview`.

## 0.3.14 Start visibility

Native presentation tests: 43/43 passed. Focused real-ROM Start visibility runtime tests: 46/46 passed for each edition, after 1,424 FireRed / 1,426 LeafGreen native-data checks. Covers default suppression, option off, companion disconnect/unready/disabled, inline display fallback, Safari, exit confirmation, and unknown overlays. Run `gen3_runtime_test.lua` with `FRLG_START_VISIBILITY_ONLY=1` for this focused suite. The full runtime suite on this local host encounters an unrelated pointer test requiring a newer `Input:mousepressed` API; it is not claimed as passing. Physical-device testing remains outstanding.

## 0.3.15 — Fly Teleport

Adds the optional Fly Teleport tile and companion menu routing. Both-edition collection suites pass 362 checks each, including tile insertion, launch, disable/uninstall hiding and restoration. Package validate/lint/gen3check pass; physical device testing remains outstanding.

## 0.3.16 — Collection touch support

595/595 collection/touch checks per edition. Native runtime, pointer, control, route, progress and online regressions pass. Real LÖVE-rendered layouts were inspected; physical-device testing remains outstanding. See [touch coverage](../../docs/TOUCH-SUPPORT.md).
