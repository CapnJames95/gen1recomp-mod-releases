# Disable L/R Help 0.1.0

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Disables the native FireRed/LeafGreen **L/R Help** screen and the engine's **L=A** alias while enabled. L/R presses are not consumed or rebound, so existing menu navigation and mod hotkeys still receive them. Other mods' Help-update handlers are preserved rather than skipped.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

**ENABLED** defaults to on. Disable it to restore native Help and the saved L=A behavior. The mod never rewrites your button mode or controller/keyboard mappings. If Help is already open when enabled, it closes using native cleanup. An edition reset cannot re-enable Help while this mod remains active.

This frees the buttons from Help, but does not assign hotkeys or resolve competing L/R bindings between other mods. Native shoulder-button actions such as menu page navigation remain available. Uses whichever keyboard/controller bindings already map to L/R.

## UI and compatibility

No replacement overlay or custom UI. Existing LegalMon-style mod panels remain unchanged. For example, the separate Party Held Items mod can still use its L shortcut:

![Existing Party Held Items L-hotkey panel, not a new overlay](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-effect-firered-party-items.png)

API 2, `engine_internals`, FireRed/LeafGreen beta. Tested against upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`; private interfaces may change. Third-party mods directly replacing Help or input functions may conflict. No ROM, extracted game assets, player saves or mappings are packaged. See [VALIDATION.md](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/disable-lr-help/VALIDATION.md).
