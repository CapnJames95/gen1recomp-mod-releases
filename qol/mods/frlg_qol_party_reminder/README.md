# Party Move Reminder

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Open the move reminder from the party list with the original FRLG mushroom payment.

Three-game suite component. Current automated checks use gen1recomp 0.3.39; complete gameplay validation remains deferred. Older validation reports describe their original FRLG snapshots.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

On the normal party list press START (default Escape). Costs two Tiny Mushrooms, otherwise one Big Mushroom, only after learning. Cancel/no eligible move costs nothing. FRLG uses mushrooms; Emerald uses one Heart Scale. The separate Pokémon Services reminder is free. Available wherever the normal party menu opens.

Options are in this mod's manager entry. ENABLED turns its behavior off. Mods with tools share one START > QOL menu automatically; there is no required central package.

## Compatibility

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. Declares `engine_internals` because the public API lacks the necessary narrow extension point. Other mods replacing the same functions may conflict. Inactive wrappers fall through after the loader changes; restart fully after a load error. Online/arena play is outside this package's scope. No ROM, graphics, audio or extracted data included.

## Validation

See VALIDATION.md and the collection's tests/ for the ROM-free checks and the exact limitations. For standalone checking, use upstream `tools/modkit.py lint` and `validate` on this directory.

## In-use UI examples

These are native UI renders from real mod hooks with isolated fixture data, not a live-play recording.

Pressing START in the party list opens the native move reminder when a Big Mushroom is available.

![Party Move Reminder in use](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-effect-firered-party-reminder.png)

**Observed 0.1.0 limitation:** the Tiny Mushroom lookup uses `TINY MUSHROOM`, but the real imported item is `TINYMUSHROOM`; two Tiny Mushrooms are not recognized in the tested cache. The Big Mushroom path opens correctly. The release has been preserved unchanged; use one Big Mushroom until this is fixed.

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Party Move Reminder details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_party_reminder-detail.png)

![Party Move Reminder options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_party_reminder-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
