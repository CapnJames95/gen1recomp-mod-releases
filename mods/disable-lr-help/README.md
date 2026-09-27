# Disable L/R Help 0.1.0

Disables the native FireRed/LeafGreen **L/R Help** screen and the engine's **L=A** alias while enabled. L/R presses are not consumed or rebound, so existing menu navigation and mod hotkeys still receive them. Other mods' Help-update handlers are preserved rather than skipped.

## Install

Import `disable-lr-help-0.1.0.zip` in **MODS → Import mod .zip**, enable **Disable L/R Help**, then restart. Alternatively place this folder directly in the game's mods directory. Works independently; no shared QoL package required.

**ENABLED** defaults to on. Disable it to restore native Help and the saved L=A behavior. The mod never rewrites your button mode or controller/keyboard mappings. If Help is already open when enabled, it closes using native cleanup. An edition reset cannot re-enable Help while this mod remains active.

This frees the buttons from Help, but does not assign hotkeys or resolve competing L/R bindings between other mods. Native shoulder-button actions such as menu page navigation remain available. Uses whichever keyboard/controller bindings already map to L/R.

## UI and compatibility

No replacement overlay or custom UI. Existing LegalMon-style mod panels remain unchanged. For example, the separate Party Held Items mod can still use its L shortcut:

![Existing Party Held Items L-hotkey panel, not a new overlay](../../docs/screenshots/qol-effect-firered-party-items.png)

API 2, `engine_internals`, FireRed/LeafGreen beta. Tested against upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`; private interfaces may change. Third-party mods directly replacing Help or input functions may conflict. No ROM, extracted game assets, player saves or mappings are packaged. See [VALIDATION.md](VALIDATION.md).
