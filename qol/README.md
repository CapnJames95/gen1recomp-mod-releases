# FRLG QoL Suite

The [QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md) is the only installable QoL package, containing 32 individually configurable components, with 31 applicable in each of Emerald, FireRed and LeafGreen. [Download and installation](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/PACKAGES.md). Disable older standalone packages and restart before using it.

Use **START → QOL → QOL SETTINGS** for feature toggles/options and **QOL SHORTCUTS** for configurable bindings with context descriptions. Dual Screen requires 0.3.21+.

The `mods/` folders here contain component documentation. Runtime code is included in the suite ZIP. They are not separate distributed mods. Component manager previews have been refreshed from current source; older test reports are labelled historical. Use the suite menus for installed settings.

## Main controls

| Feature | Control |
| --- | --- |
| Running from start | Hold B |
| Party nickname / move reminder / held items | SELECT / START / L in the normal party list |
| Summary nature + optional IV/EV | SELECT, outside battle |
| Wild-battle Ball shortcut | F7 / Y / SELECT: Throw or Select Ball menu; configurable bindings |
| Town Map service notes | SELECT on an idle Town Map or Fly map |
| Hold fast-forward | F9 or L3 by default; 2×/4×/8× is configurable |

Controls are logical game buttons except the explicitly configured fast-forward key. In custom panels, up/down selects and left/right pages; A chooses and B closes. No bulk-release shortcut is added.

## LegalMon styling

New custom panels use the LegalMon reference's 240×160 layout, blue title bar, subtle striped backdrop, native FRLG font and player-selected frame, pale-blue selected row, and framed help footer. The shop/battle overlays use the same colors and frames. Each mod carries its own identical helper; LegalMon itself is not a dependency and was not modified.

Existing engine screens reused for naming, move replacement, the native move reminder, saves and other normal gameplay keep their edition’s native rendering. This is not a whole-game UI reskin.

When added mods make the Start menu exceed nine entries, the tool packages provide a LegalMon-style paged view while preserving native actions and cursor handling. Co-loading with your local LegalMon package passed loader/menu checks on both editions. The party-item L shortcut takes precedence over native Help only while the normal party list is the top screen.

## What is—and is not—done

See [the complete request checklist](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/STATUS.md), [engine-owned features](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/ENGINE_FEATURES.md), and [upstream/community research](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/RESEARCH.md).

Many requested behaviors already exist in this FRLG engine; they are not repackaged as no-op mods. Some extensions are intentionally narrow: field HMs require the owned HM, a non-egg party member, badges and valid terrain; saving retains the actual write and failure handling.

## Validation and safety

Read [VALIDATION.md](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/VALIDATION.md) before use. Current automated checks cover all three games; older component reports cover the two FRLG editions, loader teardown/reload and exclusions. Additional tests use existing imported FireRed and LeafGreen data read-only, and native draw traces were inspected against LegalMon. **This is not an end-to-end interactive gameplay certification.** Beta-specific private APIs require care.

The source and packages contain no ROMs, extracted game graphics, audio, map data or species tables. No existing save was opened or modified by validation. New game progress made while using a mod is not undone by uninstalling it.

Source is in `mods/`, reproducible checks in `tests/`, machine-readable modkit results in `check-results.json`, and the single installable [QoL Suite ZIP](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-qol-suite-0.3.9.zip).

## Screenshot gallery

Each individual mod README includes native detail and options screenshots. The [collection README](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/README.md#qol-suite-features) lists every mod with its feature description and image.

## Additional QoL assistants

Quick Heal Party and Capture Assistant are included in the QoL package index and downloads. Their IDs and settings are unchanged. Dual Screen 0.3.4 gives both dedicated Home tiles instead of Live QoL toggles; each opens the mod’s own controls.
