# Current validation — Gen3DualScreen 0.4.14

Current combined collection/touch checks pass **4,367 in FireRed, 4,367 in LeafGreen and 4,233 in Emerald** on gen1recomp 0.3.39. Coverage includes Emerald PokéNav routing/acquisition guards, black upper-viewport ownership, isolated native navigation rendering, and removal of the Start size/position editor. The Mac and Thor QoL Test installations have 275 mod files verified each, with saves/settings preserved. Full gameplay validation and Thor confirmation of the navigation flicker fix remain pending. [Current evidence and limits](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md) · [Screenshot provenance](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/SCREENSHOTS.md).

## Historical test records

Versions, counts and installation statements below refer to earlier runs, not the current installed build.

# Validation — 27 September 2026

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


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

595/595 collection/touch checks per edition. Native runtime, pointer, control, route, progress and online regressions pass. Real LÖVE-rendered layouts were inspected; physical-device testing remains outstanding. See [touch coverage](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/TOUCH-SUPPORT.md).

## Home editing — 29 September 2026 / 0.3.17

All 16 selected FireRed/LeafGreen suites passed; collection integration now has 371 checks per edition. The actual editor test moves a full-width Team widget onto occupied app tiles, checks every placement, restores all positions with Undo, and exits with Done. Layout tests perform 120 repeated mixed-size moves (full-width, seven-column and two-row widgets) and verify no overlaps, lost tiles or mutation of the Undo copy. The GPU preview was inspected for selected-widget feedback, instructions, Undo/Done and the completed move. Physical Thor interaction remains unverified.

## Contextual FIELD tile — 29 September 2026 / 0.3.18

All 16 native-data suites passed across FireRed and LeafGreen. The collection suite now passes 396 checks per edition, including 25 new checks covering native move/badge restrictions, eggs, terrain, Waterfall direction, rod ownership, stale eligibility and busy-world rejection. The actual native Party-menu selection and Field dispatcher are exercised for Fly; the RegionMap.show boundary is intercepted to verify Fly mode and its destination callback without starting a world fixture.

The LÖVE preview uses the actual Home renderer with synthetic locked, waterside and cave section states; borders, labels and section spacing were inspected. This does not constitute an AYN Thor hardware test. Native animation completion and every field-action confirmation have not been manually played through.

## Field execution regression — 29 September 2026

The native-data collection suite passes 559 checks per edition on official dev `5540fc1`, including execution/access checks for the FIELD tile, legacy Tools and Field Kit. Runs cover both menus with owned, untaught HMs and the tile with taught moves while Field Kit is disabled. Native dispatch reaches Cut's object-removal callback, Flash's flag and zero darkness level, Waterfall's movement and crest completion, and all three rod tiers' native fishing state and Bag exit. Badge, egg, absent-HM, stale-selection and waterfall-fishing restrictions are covered.

Tests use synthetic terrain/objects and replace the Pokemon presentation callback and physical step adapter; native Party/Bag dispatch and effect state machines run. These are not full fishing battle or hardware playthroughs. All 16 companion suites passed across both editions. The focused Field Kit behavior suite also passes. The broad QOL runner's pre-existing identical-support-file assertion fails before running tests; no unrelated support files were changed.

Home visibility checks cover standard and large tiles, position preservation, enabling an unplaced widget, Options protection, and settings pagination. The native LÖVE settings preview was inspected. Runtime/control/online suites now pass 959/1405/1056 checks per edition; the collection suite passes 559 per edition. No AYN Thor hardware test was performed.

## Tile label clarification — 0.3.20

Settings now distinguish app shortcuts, wide panels and standard action tiles. The actual LÖVE settings renderer was inspected; the FireRed collection preview passed 559 checks, strict fixture validation passed, and existing saved tile IDs/visibility were preserved. This is a label-only change.

## QoL Suite integration — 0.3.21

The combined package passes 50 suites against installed Gen1recomp 0.3.31, including 532 native-data collection checks per edition. Menu previews using native fonts were visually inspected. See [QoL Suite validation](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/VALIDATION.md) for exact scope. Earlier broad companion suites above were not all rerun; physical-device verification remains outstanding.

## 0.3.22 regression checks

Both editions pass the combined collection tests, including absent HM catalog surfaces, contextual Strength eligibility, shortcut Fly cancellation to field and unchanged ordinary Party return. No device test is claimed for this update.

## 0.3.25 Field widget removal

All 56 combined suites pass across FireRed and LeafGreen, including 637 companion checks per edition. The retired Field surface is absent from Home, tile settings and the store; saved layout placement rejects it. Latest remote shortcut/field fixes remain included.

## 0.3.26 Flash tile

All 56 combined suites pass across both editions. New checks cover tile creation and dark/lit/missing-state/non-cave/already-active/badge/capability gates. Existing native Flash execution checks pass. Manual Thor gameplay testing remains outstanding.

## 0.4.0 — Kanto Gear 3.4.0 and experimental Emerald

Integrated upstream release v3.4.0 at `247187dcb15c8e9f0ebd36f78bb8a960d23ab203`, using v3.3.3 as the three-way merge base. The fork keeps its identity, FRLG presentation, mod integration, dedicated Flash tile, removed Field widget and user shortcut defaults. Added a Profile API fallback for the earlier FRLG host and used the host's Gen 3 manifest group so older loaders do not reject an unknown Emerald game identifier.

On official host v0.3.39 (`faa6a02fc84de4adf7c640eec19aa900dba9637c`), all 16 pre-existing native suites and eight added dialogue/full-battle/menu-refresh/naming suites passed across FireRed and LeafGreen. The combined QoL/companion runner passed all 56 suites. An additional LeafGreen runtime run on the previous local FRLG host passed 959 assertions after the compatibility fallback.

Emerald native/runtime/summary tests and the shared UI cases are retained and adapted to this fork's mod ID. Run `tools/frlg-dual-screen/check.py --editions emerald` with a 0.3.33+ host and an Emerald import. **Emerald native-data testing now passes:** 3,959 native checks; runtime 159, summary 237, dialogue 180, full battle 303, menu refresh 169 and naming 653 assertions. Tests use the user’s local import without distributing ROM data. No device playthrough or post-merge Thor UI check is claimed. Other collection packages remain FRLG-only.
