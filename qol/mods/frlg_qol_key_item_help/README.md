# Key Item Help 0.1.2

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Explain useful key items after acquisition and in Bag descriptions.

Current suite component on gen1recomp 0.3.39; earlier validation reports are historical.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

Bag descriptions use compact, explicit line breaks: at most three lines, each within 192 pixels of the native 200-pixel text area. The fuller acquisition help remains unchanged. This fixes text extending beyond the Bag screen without shrinking the font or changing the native layout.

Historical preview (older build): [All nine corrected Bag descriptions](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/key-item-help/firered-bag.png).

Authored guidance replaces descriptions for Bicycle, Town Map, VS Seeker, Itemfinder, three rods, Poke Flute and Silph Scope. First acquisition through Bag.add queues a LegalMon-style help panel after scripts, movement and other UI finish. ACQUISITION HELP disables popups. Existing saves do not trigger retroactive popups. Unknown items retain native descriptions. Direct inventory writes bypass this notification. VS Seeker Readiness takes priority for that item's description when both mods are enabled.

ENABLED disables this mod. Restart after enabling, disabling or updating.

## Compatibility and validation

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. Uses private engine extension points with declared engine_internals permission. May conflict with replacements of the same functions. Online/arena play is unsupported. New panels match LegalMon's blue header, native frame and selection palette. No ROM assets/data included. See VALIDATION.md for exact checks and limitations; not interactive-gameplay certified.

## In-use UI examples

These are native UI renders from real mod hooks with isolated fixture data, not a live-play recording.

The mod’s native help panel explains the Bicycle and registered-item shortcut.

![Key Item Help in use](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-firered-key-help.png)

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Key Item Help details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_key_item_help-detail.png)

![Key Item Help options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_key_item_help-options.png)

Native UI example from the development render harness:

![Key Item Help UI](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-firered-key-help.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
