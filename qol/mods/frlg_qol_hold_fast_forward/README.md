# Hold Fast Forward

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Temporarily speed up gameplay while holding a spare keyboard key.

Three-game suite component. Current automated checks use gen1recomp 0.3.39; complete gameplay validation remains deferred. Older validation reports describe their original FRLG snapshots.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

Hold F9 or L3 by default; choose 2x/4x/8x. Legacy keyboard/controller choices remain available. Releasing restores native category speed immediately, without changing settings. Respects the engine's speed locks. Controller speed up/down and touch hold are already native.

Options are in this mod's manager entry. ENABLED turns its behavior off. Mods with tools share one START > QOL menu automatically; there is no required central package.

## Compatibility

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. Declares `engine_internals` because the public API lacks the necessary narrow extension point. Other mods replacing the same functions may conflict. Inactive wrappers fall through after the loader changes; restart fully after a load error. Online/arena play is outside this package's scope. No ROM, graphics, audio or extracted data included.

## Validation

See VALIDATION.md and the collection's tests/ for the ROM-free checks and the exact limitations. For standalone checking, use upstream `tools/modkit.py lint` and `validate` on this directory.

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Hold Fast Forward details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_hold_fast_forward-detail.png)

![Hold Fast Forward options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_hold_fast_forward-options.png)

## Compatibility update (0.2.0)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
HOLD BUTTON adds L3/R3 or shoulder choices, OFF by default. Uses connected SDL gamepad state, stops on release/disconnect/focus loss, and preserves native speed locks. Choose an otherwise-unused button; other button actions are not remapped.

## Touch hold — 0.2.1

With Gen3DualScreen 0.3.16, open LIVE QOL SETTINGS and hold HOLD TO FAST FORWARD. Release or slide off to return to normal speed. Focus loss, page changes and session changes also end the hold. Existing keyboard/controller bindings and speed-lock restrictions still apply.
