# Sorted Bag

Sort displayed pocket rows without rewriting saved inventory.

Experimental FRLG beta mod for players. Source-tested against upstream commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`; not ROM-playtested.

## Install

Import this mod's ZIP through the launcher's MODS > Import mod .zip, enable it, and restart the game. Alternatively place this entire folder under `mods/frlg_qol_bag_sort/`. Install each desired mod separately; no common mod is required. Restart after enabling/disabling or updating. Keep a backup of your save when testing beta mods.

## Use and configuration

Sort by name, descending quantity, or numeric item ID. Pocket assignment stays native. TM Case and Berry Pouch have separate renderers and are not reordered. Manual bag ordering is hidden while enabled; disable to restore it.

Options are in this mod's manager entry. ENABLED turns its behavior off. Mods with tools share one START > QOL menu automatically; there is no required central package.

## Compatibility

FireRed and LeafGreen only, using the shared FRLG engine. Declares `engine_internals` because the public API lacks the necessary narrow extension point. Other mods replacing the same functions may conflict. Inactive wrappers fall through after the loader changes; restart fully after a load error. Online/arena play is outside this package's scope. No ROM, graphics, audio or extracted data included.

## Validation

See VALIDATION.md and the collection's tests/ for the ROM-free checks and the exact limitations. For standalone checking, use upstream `tools/modkit.py lint` and `validate` on this directory.

## In-use UI examples

These are native UI renders from real mod hooks with isolated fixture data, not a live-play recording.

Before: original inventory order.

![Sorted Bag in use](../../../docs/screenshots/qol-effect-firered-bag-before.png)

After: alphabetical rows, with the same item quantities.

![Sorted Bag in use](../../../docs/screenshots/qol-effect-firered-bag-sorted.png)

## Screenshots

Native FRLG mod-manager renders from the loaded 0.1.0 package in an isolated test session. These show the real detail/options UI; they are not live gameplay captures.

![Sorted Bag details](../../../docs/screenshots/frlg_qol_bag_sort-detail.png)

![Sorted Bag options](../../../docs/screenshots/frlg_qol_bag_sort-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Independently installable; restart after replacement.
