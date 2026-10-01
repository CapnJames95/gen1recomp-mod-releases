# Current 0.2.4 checks

Six native-engine integration runs pass on 0.3.42: Field Kit menu and Dual Screen tile in FireRed, LeafGreen and Emerald. Untaught Sweet Scent starts a real battle with unchanged moves/PP. Eggs, disabled component, old engine, unrelated party and invalid terrain are rejected. Cut still requires its HM; Dig still requires learning. [Reproduction and limits](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/SWEET-SCENT-RETEST.md#hm-field-kit-024-integration).

## Earlier evidence

# Validation — HM Field Kit

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md) and [three-game status](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


Target: official bryanthaboi/gen1recomp dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`.

This package passed its ROM-free behavior suite on FireRed and LeafGreen, combined loading with the other 25 packages, strict upstream fixture validation, content lint, Gen 3 static checking, and ZIP packaging. Static scans can leave private wrapper calls unresolved; a load pass is not proof of runtime behavior.

The collection also passed 33 imported-data checks per edition and seven adjacent upstream baseline scripts. Those are focused checks, not a complete in-game test of this package. No full interactive playthrough, controller hardware, online/arena, or community-mod combination certification was performed.

New custom panels match the user's LegalMon reference. Reused built-in game dialogs remain native. No ROM data, extracted assets or player saves are distributed. Back up your save and restart after changing mods. Private engine APIs can break in later beta builds.

The full collection contains `tests/`, `check-results.json`, `STATUS.md` and `VALIDATION.md` with the complete scope and reproduction instructions. Source-only standalone rechecking uses the official engine's `tools/modkit.py lint`, `validate --base fixture --strict`, and `gen3check`, with MODKIT_LUAJIT set to your LuaJIT executable.
## Compact Start fallback 0.1.2

The Start-menu overflow fallback now delegates to native drawing with a right-aligned, at-most-14-tile-wide viewport of nine rows. The complete entry list, cursor and template are restored even after drawing errors. Scrollable Start Menu retains priority; a hidden Dual Screen Start menu remains hidden. Short menus and Safari retain their existing renderer.

Validated with tools/start-menu-fallback-test.lua on FireRed and LeafGreen, both helper installation orders: 1,108 passing assertions covering every cursor position, label bounds, callback identity/selection, confirmation, error restoration, disable/unload/reload, short menus and dedicated-renderer priority. Existing HM/Dex behavior checks: 30 passing assertions across both editions. Native offscreen LeafGreen preview loaded 36 mods with Dual Screen and Scrollable Start Menu excluded. No live save was used.

## Flash and lighting 0.2.0

Tested against local engine commit `5540fc1` with the real field-move and field-view modules and synthetic map/party fixtures: 30 assertions per edition (60 total), covering HM ownership and compatibility, no injected move, badge/terrain/already-used gates, caller-context preservation, lighting on/off, non-cave rendering, native and saved level preservation, real Flash state, disable/unload and other-game fallthrough. Strict fixture validation and content lint pass. Gen 3 static checking reports loadable, with four unresolved wrapper/module references. No Windows/device cave playtest has been performed.

## Field execution regression — 29 September 2026

The native-data collection suite passes 559 checks per edition on official dev `5540fc1`, including execution/access checks for the FIELD tile, legacy Tools and Field Kit. Runs cover both menus with owned, untaught HMs and the tile with taught moves while Field Kit is disabled. Native dispatch reaches Cut's object-removal callback, Flash's flag and zero darkness level, Waterfall's movement and crest completion, and all three rod tiers' native fishing state and Bag exit. Badge, egg, absent-HM, stale-selection and waterfall-fishing restrictions are covered.

Tests use synthetic terrain/objects and replace the Pokemon presentation callback and physical step adapter; native Party/Bag dispatch and effect state machines run. These are not full fishing battle or hardware playthroughs. All 16 companion suites passed across both editions. The focused Field Kit behavior suite also passes. The broad QOL runner's pre-existing identical-support-file assertion fails before running tests; no unrelated support files were changed.
