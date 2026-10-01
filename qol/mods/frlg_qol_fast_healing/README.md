# Faster Center Healing 0.2.0

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Speed up Center healing and remove the idle wait for the healing jingle.

Experimental FRLG beta mod for players. Tested against upstream commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`; not device-playtested.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

Choose animation speed 2x/4x/8x (default 4x). **WAIT FOR JINGLE** defaults to **OFF**: once the accelerated machine animation finishes, the nurse continues immediately instead of waiting for the full sound. The jingle plays out normally in the background; music restoration and unrelated fanfare waits are unchanged. Turn WAIT FOR JINGLE on to restore the original sound wait. Healing, dialogue, script progression and completion callbacks remain native; this does not skip prompts or heal the party early.

Options are in this mod's manager entry. ENABLED turns its behavior off. Mods with tools share one START > QOL menu automatically; there is no required central package.

## Compatibility

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. Declares `engine_internals` because the public API lacks the necessary narrow extension point. Other mods replacing the same functions may conflict. Inactive wrappers fall through after the loader changes; restart fully after a load error. Online/arena play is outside this package's scope. No ROM, graphics, audio or extracted data included.

## Validation

See VALIDATION.md and the collection's tests/ for the ROM-free checks and the exact limitations. For standalone checking, use upstream `tools/modkit.py lint` and `validate` on this directory.

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Faster Center Healing details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_fast_healing-detail.png)

![Faster Center Healing options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_fast_healing-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
