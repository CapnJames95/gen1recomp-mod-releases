# Current validation — QoL Suite 0.3.9

Current combined collection/touch checks pass **4,367 in FireRed, 4,367 in LeafGreen and 4,233 in Emerald** on both gen1recomp 0.3.39 and 0.3.42. Six additional 0.3.42 integration runs verify untaught Sweet Scent through Field Kit and the Dual Screen tile across all three games. Coverage includes Emerald PokéNav routing/acquisition guards, black upper-viewport ownership, isolated native navigation rendering, and removal of the Start size/position editor. The Mac and Thor QoL Test installations have 275 mod files verified each, with saves/settings preserved. Full gameplay validation and Thor confirmation of the navigation flicker fix remain pending. [Current evidence and limits](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md) · [Screenshot provenance](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/SCREENSHOTS.md).

## Historical test records

Versions, counts and installation statements below refer to earlier runs, not the current installed build.

## Navigation follow-up — 0.3.3

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


The 45-suite three-game check passes. Additional navigation regressions exercise real Dex/tool menus, parent cursor and Start-state preservation, Back input consumption, failure notices, successful field dispatch, direct entry without Start, and Secret Base registry refresh after removal. Hardware gameplay validation remains deferred.

# QoL Suite 0.3.1 follow-up

Hoenn Tools regression covers empty-registry A/B exit without map scripts, confirmed unregister/cancel, inline bike changes, 87 safe native berry destinations, actual warp completion and challenge guards. Decoration placement is restricted to the own-base PC. Synthetic tests do not establish a hardware playtest.

# QoL Suite validation

## 0.3.0 validation

All **45** suites in `tools/emerald-port/check.py` pass on gen1recomp 0.3.39 with imported native data and synthetic saves. Additional final checks exercise real disk save/reload for starter preparations in all three games, all eight Hoenn panels through Dual Screen touch, and the direct Feebas-to-Shiny-Hunter entrypoint. Native Feebas comparison covers 446 water tiles, including six valid tiles for the test seed; previews preserve Pokémon and encounter RNG.

`tools/build-qol-suite.py --check` verifies all 32 canonical component implementations. Collection validation checks ZIP integrity, source agreement, bundle equality, screenshot files and local links. New native menu previews use synthetic state and were visually inspected.

Gameplay validation is deferred by request. Thor performance is reported excellent; this update has not been installed on either device. No new PKHeX batch run is claimed.

## Historical validation

Historical validation, 29 September 2026. Tested with LuaJIT 2.1 and an isolated copy of installed Gen1recomp **0.3.31**. Loader SHA-256 and per-suite outcomes are recorded in results. The ROM-free tests also passed on upstream revision `6d224e7d898bb347d7e382369955405cddd4516c`.

The runner passes **56 suites, zero failures**, across FireRed and LeafGreen: 23 original small-QoL behaviour suites, one combined-loader integration suite and one native-data collection suite and three added-component native suites per edition. Original behaviour tests run through the actual suite loader with other features disabled. Combined integration enables every feature and the actual Dual Screen package.

The combined-loader suite passes **288 checks per edition**: all 31 initializers, legacy settings, persistence/events, menu navigation and touch geometry, invalid settings, master/component/host disables, reload/unload, duplicate installation conflicts, companion startup, all 31 Live QoL rows, assistant Home availability, contextual shortcuts, fast-forward discovery, ball-picker mutual exclusion and Summary IV routing.

The native collection suite passes **550 checks per edition** with all 8 installable packages, using imported game data and freshly generated sessions. It covers companion routing, Home tiles, controls, native menus, capture assistance, HM/rod eligibility and native field dispatch. Native-data setup separately passes 1,424 FireRed / 1,426 LeafGreen checks; these setup counts are not additional collection checks. User saves and installed settings were not touched.

Dual Screen also passes its original standalone collection regression: **559 checks per edition**, with the suite excluded. Logs are retained beside the combined results.

Eight additional baseline runs passed against the unchanged original implementations: Summary IVs (188 checks per edition), party assistants (140), Disable L/R Help (76), and Scrollable Start's native HUD/storage/reload integration. See outcomes and corresponding logs. These baseline runs use standalone implementations; bundled wiring is covered by the combined tests above.

The existing Ball Shortcut test was updated to reflect already-shipped 0.2.2 behaviour: physical hotkeys open SELECT BALL; backing out visits the action menu before closing. The old assertion failed for the standalone mod as well. The implementation is unchanged.

`components.json` records source versions and SHA-256 hashes. The build check compares all 31 implementations byte-for-byte against their canonical standalone sources and checks the installable ZIP. Modkit validation, lint and Gen3 checks on the extracted installable ZIP complete without errors; Dual Screen retains an engine-internals compatibility warning. Native-font menu and options draw traces were rendered and visually inspected.

## Reproduce

From the collection root, using an engine checkout containing its test harnesses:

```sh
python3 mods/frlg-qol-suite/tests/run.py --engine /path/to/gen1recomp --lua /path/to/luajit --cache-root /path/to/pokemon-love2d
python3 tools/build-qol-suite.py --check
```

Omit `--cache-root` for the 48 ROM-free suites. Detailed logs accompany the machine-readable results.

## Remaining verification

No physical AYN Thor test or extended live gameplay session was performed for this change. Native tests use synthetic world/session state; they do not establish every capture/egg outcome or hardware rendering behaviour. No new PKHeX run is claimed because Pokémon generation implementations were not changed. 

## 0.1.1 regression checks

The combined tests additionally cover nested QOL entries, ten shortcut pages, context descriptions, persisted edits, logical-button remapping, keyboard/pad/trigger dispatch, repeat suppression, release handling and out-of-context fallthrough. The native capture harness exercises suite-only Start drawing through full upward/downward loops and wraparound, checks cursor/label agreement and restored native scroll state, and checks inspector IV/EV remapping. The standalone Scrollable Start native HUD/storage suite includes the same bidirectional render regression. Both editions pass. Shortcut pages were rendered with native fonts and visually inspected.

Component payloads still match their canonical sources byte-for-byte. In this update Scrollable Start's renderer and Capture Help's explanatory text were intentionally updated; the prior claim that every implementation was unchanged describes 0.1.0.

## 0.1.2 navigation regression

Combined tests verify QOL retains the existing Start layer, Settings and Shortcuts return through QOL, cursor/scroll/layout identity survives Back, and START closes the whole chain with one close callback.

## 0.1.3 expanded suite

Pokemon Services, Fly Teleport and Day Care Viewer are included byte-for-byte. Both-edition integration checks exercise their standalone conflicts in both load orders. Native collection tests cover Start entries, persistent enable/disable switches, opening the original panels, Back retaining Start, and companion Home discovery/disable/routing for all three additions. Day Care Viewer receives an enabled option from the suite adapter. No Pokemon-generation implementation was changed.

The added native baseline suites pass Services 194, Fly Teleport 291 and Day Care Viewer 82 checks per edition. Services/Teleport test fixtures now clear the synthetic startup warp when establishing idle field state on engine 0.3.31; production runtime code is unchanged.

## 0.1.4 Quick Field Actions

All 56 suites in `tests/run.py` pass against the local official engine checkout for FireRed and LeafGreen with imported-data integration enabled. Quick Field Actions passes 88 native-interaction assertions per edition (176 total). These tests use synthetic targets and stub final animation execution; manual device testing of the four added actions remains outstanding.

## 0.1.5 regression checks

Both editions pass 56 suites with no failures. HM Kit adds boulder-target and already-active Strength regressions. Dual Screen field tests cover HM tile removal and Fly return ownership. Activation bindings are unchanged.

## 0.1.6 engine 0.3.36

All 56 suites passed against the engine payload copied from the Thor (0.3.36). Regressions cover consumed Back edges, hidden/disabled ball shortcuts with the companion installed, preference restoration after removal, and fullscreen Fly ownership while the map is routed below. Intermittent hardware flicker still needs user confirmation on the Thor.

## 0.1.7 shortcut regressions

Fast Forward defaults to F9 (keyboard) and L3 (controller). Dual Screen screen swap uses F6 only; Y is reserved for its ball picker. Overlay visibility defaults to R3 in overlay mode. Ball picker remains F7/Y, Capture Help remains R, and Trigger Tabs remains off. Existing saved overrides are preserved unless explicitly changed.

Regression checks cover F9/L3 defaults, Right Ctrl falling through, Y not swapping, F6 edge handling and R3 overlay activation.
