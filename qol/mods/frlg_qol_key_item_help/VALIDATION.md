# Validation — Key Item Help 0.1.2

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md) and [three-game status](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


## Bag overflow fix

Target: official engine `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. The native Bag draws descriptions at (40,115), width 200, line pitch 14, without word wrapping. This mod now supplies a separate compact, line-broken string rather than its full acquisition prose.

42 fixture assertions pass per edition (84 total): all nine descriptions fit three lines, line widths are bounded, unrelated/disabled descriptions remain native, and full acquisition help and queue behavior are preserved. An additional 31 native-font bounds checks pass per edition (62 total) using the user's imported caches. All nine items were rendered through the native Bag in each edition and both contact sheets visually inspected; no text crosses the screen edge. No ROM assets are packaged and no player saves are used.

Reproduce the native-font checks and captures with `tools/key-item-help/capture.lua`, passing collection root, edition, imported cache path and output directory from the engine checkout. Render the resulting traces with `tools/render-manager-traces.py`. Physical-device playthrough testing is not claimed.

## Historical validation

Target: official bryanthaboi/gen1recomp dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`.

This package passed its ROM-free behavior suite on FireRed and LeafGreen, combined loading with the other 25 packages, strict upstream fixture validation, content lint, Gen 3 static checking, and ZIP packaging. Static scans can leave private wrapper calls unresolved; a load pass is not proof of runtime behavior.

The collection also passed 33 imported-data checks per edition and seven adjacent upstream baseline scripts. Those are focused checks, not a complete in-game test of this package. No full interactive playthrough, controller hardware, online/arena, or community-mod combination certification was performed.

New custom panels match the user's LegalMon reference. Reused built-in game dialogs remain native. No ROM data, extracted assets or player saves are distributed. Back up your save and restart after changing mods. Private engine APIs can break in later beta builds.

The full collection contains `tests/`, `check-results.json`, `STATUS.md` and `VALIDATION.md` with the complete scope and reproduction instructions. Source-only standalone rechecking uses the official engine's `tools/modkit.py lint`, `validate --base fixture --strict`, and `gen3check`, with MODKIT_LUAJIT set to your LuaJIT executable.
