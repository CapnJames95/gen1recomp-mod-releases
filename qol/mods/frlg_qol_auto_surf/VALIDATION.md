# Validation — Quick Field Actions 0.3.0

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md) and [three-game status](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


## Quick Field Actions update

The suite-loader behavior tests pass **88 assertions per edition (176 total)**, exercising native A-button interaction and eligibility for Surf, Cut, Strength, Rock Smash and Waterfall. Checks cover action payloads, targets, Strength flags, badge/move gates, disabled/non-A/UI/script cases, and Waterfall surfing, facing and tile requirements. All **56 broader suite checks pass** across FireRed and LeafGreen, including native-data companion integration. Animation execution is delegated to the engine; these additions have not been manually tested on AYN Thor.

## Historical A-button Surf update

Tested against official engine `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. The updated ROM-free suite passes **34 assertions per edition (68 total)** through the native field interaction and Surf eligibility functions with synthetic map/input fixtures. It verifies all four facing directions, no movement wrappers, no confirmation/used text, native move-user selection, badge/move requirements, land/busy/movement/surfing/bike cases, NPC/sign priority, unchanged standalone eligibility/messages, error cleanup, enable/disable and unload. Native animation execution is delegated, not device-playtested.

Strict fixture validation, lint and Gen 3 checks pass. Gen 3 analysis reports four unresolved dynamic module-passing sites, not errors. The broader QoL runner passes 50 of 52 suites, including both Auto Surf suites and both full QoL loader/reload integration suites. The two unrelated Ball Shortcut fixture suites fail at `behavior.lua:338` (false versus true); those tests run in separate processes loading only Ball Shortcut, not Auto Surf. They are not changed by this update.

## Historical validation

Target: official bryanthaboi/gen1recomp dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`.

This package passed its ROM-free behavior suite on FireRed and LeafGreen, combined loading with the other 25 packages, strict upstream fixture validation, content lint, Gen 3 static checking, and ZIP packaging. Static scans can leave private wrapper calls unresolved; a load pass is not proof of runtime behavior.

The collection also passed 33 imported-data checks per edition and seven adjacent upstream baseline scripts. Those are focused checks, not a complete in-game test of this package. No full interactive playthrough, controller hardware, online/arena, or community-mod combination certification was performed.

New custom panels match the user's LegalMon reference. Reused built-in game dialogs remain native. No ROM data, extracted assets or player saves are distributed. Back up your save and restart after changing mods. Private engine APIs can break in later beta builds.

The full collection contains `tests/`, `check-results.json`, `STATUS.md` and `VALIDATION.md` with the complete scope and reproduction instructions. Source-only standalone rechecking uses the official engine's `tools/modkit.py lint`, `validate --base fixture --strict`, and `gen3check`, with MODKIT_LUAJIT set to your LuaJIT executable.
