# Dex Companion

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Search seen species by name; read imported evolutions and wild locations; count owned species in the current area's encounter tables.

Experimental FRLG beta tool for players. Install its ZIP through launcher MODS > Import mod .zip, enable, and restart. Or copy the folder to `mods/frlg_qol_dex_companion/`. No dependency required. START > QOL > DEX COMPANION opens the tool. Directions navigate; A chooses; B closes; left/right page. Uses the original naming keyboard for search (10 characters, literal substring matching).

SHOW UNSEEN defaults off; ENABLED can disable the tool. Location and evolution details can reveal future locations once a species is seen. Locations/route completion describe imported ordinary land/water/fishing/rock-smash encounters. They do not count gifts, trades, roaming or static encounters, story availability, or runtime encounter-hook changes. Evolution rows describe extracted rules; story/National Dex gates still apply. No encounter or evolution rules are changed.

Built against upstream `84e076b2d1e2dda36073ff55ec7c311a6b97519c`. Shared FireRed/LeafGreen code, declared engine_internals permission. No ROM/assets included. Not ROM-playtested. Restart after enable/disable/update; fully restart after load errors. See VALIDATION.md. Back up saves before beta testing. Test via upstream modkit lint/validate and the collection's tests.

## In-use UI examples

These are native UI renders from real mod hooks with isolated fixture data, not a live-play recording.

Selecting a seen species shows its imported evolution rule and available wild-location records.

![Dex Companion in use](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-firered-evolution.png)

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Dex Companion details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_dex_companion-detail.png)

![Dex Companion options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_dex_companion-options.png)

Native UI example from the development render harness:

![Dex Companion UI](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-firered-dex.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
## Start menu fix (0.1.2)

Without Scrollable Start Menu, more than nine entries now use a compact right-hand scrolling sidebar instead of a full-screen panel. Native selection and callbacks are preserved. Update both HM Field Kit and Dex Companion if installed, then restart the game. No configuration changes are required.
