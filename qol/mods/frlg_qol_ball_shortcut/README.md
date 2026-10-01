# Battle Ball Shortcut

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Press Y (controller) or F7 (keyboard) to select an owned Ball from a wild single battle command menu, then confirm THROW.

Current suite component for FireRed, LeafGreen and Emerald on gen1recomp 0.3.39. Older validation reports describe historical FRLG checks; complete gameplay validation remains deferred.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

Configure Poke/Great/Ultra Ball, then SELECT (Tab/Shift) in the main command menu. No fallback to a different Ball and no Master Ball option. Empty stock falls through. Trainer, Safari, double, link, spectated and tutorial battles excluded. The battle engine still resolves the normal turn and catch.

ENABLED and any other settings appear in this mod's manager entry. Tool mods share one START > QOL menu automatically; no central dependency.

## Compatibility and tests

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. This mod declares `engine_internals`; a later beta or another mod replacing the same methods can break it. Inactive wrappers fall through after loader changes. Online/arena play excluded. See VALIDATION.md for actual checks; run upstream modkit lint/validate against this folder. No ROM-derived data or assets included.

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Battle Ball Shortcut details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_ball_shortcut-detail.png)

![Battle Ball Shortcut options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_ball_shortcut-options.png)

## Compatibility update (0.2.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
Requires Dual Screen 0.3.2 or later for companion popup ownership. Default F7 / Y; configurable key/button and optional SELECT fallback. Open, select an owned Ball, then explicitly Throw. Bottom-screen taps and physical navigation share one modal; focus loss cancels it.

## 0.2.2

Controller default is Y; keyboard default is F7. Both bindings are configurable in this mod's options and existing saved choices are preserved. These shortcuts open SELECT BALL directly; selecting a ball returns to the explicit THROW confirmation. Optional SELECT still opens the action menu. Gen3DualScreen 0.3.6 displays the current binding on its bottom battle screen. The hint hides when the shortcut is unavailable or its modal is open.
