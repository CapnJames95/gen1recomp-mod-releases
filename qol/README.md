# FRLG QoL — independent beta mods

28 independently installable mods for the official [bryanthaboi/gen1recomp](https://github.com/bryanthaboi/gen1recomp) FireRed/LeafGreen beta. These are unofficial, experimental extensions, not an engine fork.

**Target:** official dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c` (2026-09-26). Later betas may change private interfaces. Both FireRed and LeafGreen are declared in every manifest.

## September 27 compatibility update

Battle Hints and Move Inspector were removed at your request. Quiet EXP skips individual gain announcements but preserves level-ups, stat windows and move learning. Ball Shortcut 0.2.1 integrates with Dual Screen 0.3.2; update both. Shop counts now project below; Hold Fast Forward adds an optional controller hold button. All packages yield to Scrollable Start Menu 0.1.1. Restart after updating. Remove old installed `frlg_qol_battle_hints` and `frlg_qol_move_info` packages through MODS; this source cleanup does not alter your game installation.

## Install

PC Box Tools has been removed from the collection and new bundles. If previously installed, remove or disable `frlg_qol_pc_tools` through MODS and restart; copying a newer bundle does not delete an existing installation. Native PC features and Dual Screen are unchanged.

1. Back up your saves outside the game's save directory.
2. Import your own supported FireRed or LeafGreen ROM using the official engine. No ROM or extracted data is supplied here.
3. Choose individual ZIPs from [the package list](PACKAGES.md). Use launcher **MODS → Import mod .zip**, enable the desired packages, then restart.
4. Alternatively, copy selected folders from `mods/` into the game's `mods/` directory. Do not install both a source folder and a ZIP copy of the same ID.
5. Change settings in each mod's manager entry. Every package has an ENABLED switch. Restart after installation, updates or removal; restart fully after a load error.

There is **no shared dependency or required central mod**. HM Field Kit and Dex Companion share one START → QOL entry if both are installed. Options remain per-mod. Enable a few at a time when testing; avoid installing community mods that replace the same functions.

## Main controls

| Feature | Control |
| --- | --- |
| Running from start | Hold B |
| Party nickname / move reminder / held items | SELECT / START / L in the normal party list |
| Summary nature + optional IV/EV | SELECT, outside battle |
| Wild-battle Ball shortcut | F7 / R3 / SELECT: Throw or Select Ball menu; configurable bindings |
| Town Map service notes | SELECT on an idle Town Map or Fly map |
| Hold fast-forward | Right Ctrl by default; Left Ctrl or F6 and 2×/4×/8× are configurable |

Controls are logical game buttons except the explicitly configured fast-forward key. In custom panels, up/down selects and left/right pages; A chooses and B closes. No bulk-release shortcut is added.

## LegalMon styling

New custom panels use the LegalMon reference's 240×160 layout, blue title bar, subtle striped backdrop, native FRLG font and player-selected frame, pale-blue selected row, and framed help footer. The shop/battle overlays use the same colors and frames. Each mod carries its own identical helper; LegalMon itself is not a dependency and was not modified.

Existing engine screens reused for naming, move replacement, the native move reminder, saves and other normal gameplay keep their original FRLG rendering. This is not a whole-game UI reskin.

When added mods make the Start menu exceed nine entries, the tool packages provide a LegalMon-style paged view while preserving native actions and cursor handling. Co-loading with your local LegalMon package passed loader/menu checks on both editions. The party-item L shortcut takes precedence over native Help only while the normal party list is the top screen.

## What is—and is not—done

See [the complete request checklist](STATUS.md), [engine-owned features](ENGINE_FEATURES.md), and [upstream/community research](RESEARCH.md).

Many requested behaviors already exist in this FRLG engine; they are not repackaged as no-op mods. Some extensions are intentionally narrow: field HMs retain compatibility/badges/terrain; saving retains the actual write and failure handling.

## Validation and safety

Read [VALIDATION.md](VALIDATION.md) before use. Automated behavior tests cover both editions, loader teardown/reload and exclusions. Additional tests use existing imported FireRed and LeafGreen data read-only, and native draw traces were inspected against LegalMon. **This is not an end-to-end interactive gameplay certification.** Beta-specific private APIs require care.

The source and packages contain no ROMs, extracted game graphics, audio, map data or species tables. No existing save was opened or modified by validation. New game progress made while using a mod is not undone by uninstalling it.

Source is in `mods/`, reproducible checks in `tests/`, machine-readable modkit results in `check-results.json`, and directly importable ZIPs in [downloads/QOL](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest). Each mod ZIP contains a root-level `manifest.json`.

## Screenshot gallery

Each individual mod README includes native detail and options screenshots. The [collection README](../README.md#all-28-qol-tools) lists every mod with its feature description and image.

## Additional QoL assistants

Quick Heal Party and Capture Assistant are included in the QoL package index and downloads/QOL. Their IDs and settings are unchanged. Dual Screen 0.3.4 gives both dedicated Home tiles instead of Live QoL toggles; each opens the mod’s own controls.
