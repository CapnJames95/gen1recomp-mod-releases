# Party Held Items

Read all party held-item names in a compact panel.

Experimental FRLG beta mod for players; tested against upstream commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c` using ROM-free fixtures, not ROM-playtested.

## Install

Import this mod's ZIP using launcher MODS > Import mod .zip, enable, and restart. Alternatively place this entire folder under `mods/frlg_qol_party_items/`. No other package is required. Back up your save for beta testing. Restart after installing, updating or disabling; restart fully after a load error.

## Use and configuration

Press the logical L shoulder action on the normal party list (bind it in CONTROLS). Displays names without covering native HP/item icons. Read-only; giving/taking items remains native.

ENABLED and any other settings appear in this mod's manager entry. Tool mods share one START > QOL menu automatically; no central dependency.

## Compatibility and tests

FireRed and LeafGreen only. This mod declares `engine_internals`; a later beta or another mod replacing the same methods can break it. Inactive wrappers fall through after loader changes. Online/arena play excluded. See VALIDATION.md for actual checks; run upstream modkit lint/validate against this folder. No ROM-derived data or assets included.

## In-use UI examples

These are native UI renders from real mod hooks with isolated fixture data, not a live-play recording.

Pressing L in the party list opens a compact list of Pokémon and held items.

![Party Held Items in use](../../../docs/screenshots/qol-effect-firered-party-items.png)

## Screenshots

Native FRLG mod-manager renders from the loaded 0.1.0 package in an isolated test session. These show the real detail/options UI; they are not live gameplay captures.

![Party Held Items details](../../../docs/screenshots/frlg_qol_party_items-detail.png)

![Party Held Items options](../../../docs/screenshots/frlg_qol_party_items-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Independently installable; restart after replacement.
