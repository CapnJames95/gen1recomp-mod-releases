# HM Field Kit

Use owned HMs with compatible party Pokemon without teaching the move.

Experimental FRLG beta mod for players. Source-tested against upstream commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`; not ROM-playtested.

## Install

Import this mod's ZIP through the launcher's MODS > Import mod .zip, enable it, and restart the game. Alternatively place this entire folder under `mods/frlg_qol_hm_field_kit/`. Install each desired mod separately; no common mod is required. Restart after enabling/disabling or updating. Keep a backup of your save when testing beta mods.

## Use and configuration

START > QOL > HM FIELD KIT lists actions currently usable. Existing overworld Cut/Surf/Strength/Rock Smash/Waterfall checks use the same compatible-party fallback. Badge and terrain checks remain. Fly is not added to this menu: WorldAPI.flyTo is unsupported in this FRLG beta, so this package does not provide destination selection. Retain a taught Fly for the native party menu. No moveslots or flags are modified.

Options are in this mod's manager entry. ENABLED turns its behavior off. Mods with tools share one START > QOL menu automatically; there is no required central package.

## Compatibility

FireRed and LeafGreen only, using the shared FRLG engine. Declares `engine_internals` because the public API lacks the necessary narrow extension point. Other mods replacing the same functions may conflict. Inactive wrappers fall through after the loader changes; restart fully after a load error. Online/arena play is outside this package's scope. No ROM, graphics, audio or extracted data included.

## Validation

See VALIDATION.md and the collection's tests/ for the ROM-free checks and the exact limitations. For standalone checking, use upstream `tools/modkit.py lint` and `validate` on this directory.

## Screenshots

Native FRLG mod-manager renders from the loaded 0.1.0 package in an isolated test session. These show the real detail/options UI; they are not live gameplay captures.

![HM Field Kit details](../../../docs/screenshots/frlg_qol_hm_field_kit-detail.png)

![HM Field Kit options](../../../docs/screenshots/frlg_qol_hm_field_kit-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Independently installable; restart after replacement.
## Start menu fix (0.1.2)

Without Scrollable Start Menu, more than nine entries now use a compact right-hand scrolling sidebar instead of a full-screen panel. Native selection and callbacks are preserved. Update both HM Field Kit and Dex Companion if installed, then restart the game. No configuration changes are required.
