# Validation — Dex Companion

Target: official bryanthaboi/gen1recomp dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`.

This package passed its ROM-free behavior suite on FireRed and LeafGreen, combined loading with the other 25 packages, strict upstream fixture validation, content lint, Gen 3 static checking, and ZIP packaging. Static scans can leave private wrapper calls unresolved; a load pass is not proof of runtime behavior.

The collection also passed 33 imported-data checks per edition and seven adjacent upstream baseline scripts. Those are focused checks, not a complete in-game test of this package. No full interactive playthrough, controller hardware, online/arena, or community-mod combination certification was performed.

New custom panels match the user's LegalMon reference. Reused built-in game dialogs remain native. No ROM data, extracted assets or player saves are distributed. Back up your save and restart after changing mods. Private engine APIs can break in later beta builds.

The full collection contains `tests/`, `check-results.json`, `STATUS.md` and `VALIDATION.md` with the complete scope and reproduction instructions. Source-only standalone rechecking uses the official engine's `tools/modkit.py lint`, `validate --base fixture --strict`, and `gen3check`, with MODKIT_LUAJIT set to your LuaJIT executable.
## Compact Start fallback 0.1.2

The Start-menu overflow fallback now delegates to native drawing with a right-aligned, at-most-14-tile-wide viewport of nine rows. The complete entry list, cursor and template are restored even after drawing errors. Scrollable Start Menu retains priority; a hidden Dual Screen Start menu remains hidden. Short menus and Safari retain their existing renderer.

Validated with tools/start-menu-fallback-test.lua on FireRed and LeafGreen, both helper installation orders: 1,108 passing assertions covering every cursor position, label bounds, callback identity/selection, confirmation, error restoration, disable/unload/reload, short menus and dedicated-renderer priority. Existing HM/Dex behavior checks: 30 passing assertions across both editions. Native offscreen LeafGreen preview loaded 36 mods with Dual Screen and Scrollable Start Menu excluded. No live save was used.
