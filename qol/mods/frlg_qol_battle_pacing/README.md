# Battle Bar Speed

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Choose independent instant HP and EXP bars while preserving battle logic and callbacks.

Current suite component for FireRed, LeafGreen and Emerald on gen1recomp 0.3.39. Older validation reports describe historical FRLG checks; complete gameplay validation remains deferred.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

INSTANT HP and INSTANT EXP can be toggled separately. Uses upstream's own instant-tween path, retaining callbacks and display values. Move-animation on/off and overall battle speed are already engine options; animation-script time scaling is not included.

ENABLED and any other settings appear in this mod's manager entry. Tool mods share one START > QOL menu automatically; no central dependency.

## Compatibility and tests

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. This mod declares `engine_internals`; a later beta or another mod replacing the same methods can break it. Inactive wrappers fall through after loader changes. Online/arena play excluded. See VALIDATION.md for actual checks; run upstream modkit lint/validate against this folder. No ROM-derived data or assets included.

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Battle Bar Speed details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_battle_pacing-detail.png)

![Battle Bar Speed options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_battle_pacing-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
