# Validation — Faster Center Healing 0.2.0

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md) and [three-game status](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


## Jingle-wait fix

Target: official engine `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. Native `pokecenter_heal` reaches its WAIT_SOUND state after the machine animation, but the audio clock still counts real frames. Accelerating animation alone therefore left a long idle pause. This update only bypasses that machine-owned wait, not global audio completion or other scripts.

The native state-machine regression passes 29 assertions per edition (58 total): 2x/4x/8x completion with a still-playing jingle, relative durations, one completion callback, real audio state visible inside callbacks, optional sound waiting, disabled/unloaded behavior, error cleanup and invalid-speed fallback. Audio playback is stubbed in these ROM-free tests; missing-art cache warnings are expected. No physical-device playthrough is claimed.

Strict fixture validation, lint and Gen 3 static checks are run for the package. The full QoL runner's unrelated Ball Shortcut fixture failures are recorded in `outputs/fast-healing-0.2.0/qol-tests.log`; those isolated processes do not load this mod.

## Historical validation

Target: official bryanthaboi/gen1recomp dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`.

This package passed its ROM-free behavior suite on FireRed and LeafGreen, combined loading with the other 25 packages, strict upstream fixture validation, content lint, Gen 3 static checking, and ZIP packaging. Static scans can leave private wrapper calls unresolved; a load pass is not proof of runtime behavior.

The collection also passed 33 imported-data checks per edition and seven adjacent upstream baseline scripts. Those are focused checks, not a complete in-game test of this package. No full interactive playthrough, controller hardware, online/arena, or community-mod combination certification was performed.

New custom panels match the user's LegalMon reference. Reused built-in game dialogs remain native. No ROM data, extracted assets or player saves are distributed. Back up your save and restart after changing mods. Private engine APIs can break in later beta builds.

The full collection contains `tests/`, `check-results.json`, `STATUS.md` and `VALIDATION.md` with the complete scope and reproduction instructions. Source-only standalone rechecking uses the official engine's `tools/modkit.py lint`, `validate --base fixture --strict`, and `gen3check`, with MODKIT_LUAJIT set to your LuaJIT executable.
