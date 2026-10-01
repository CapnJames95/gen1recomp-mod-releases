# HM Field Kit

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Use owned HMs with any non-egg party Pokémon, even if its species cannot learn the move. The HM must be in your bag; badge and terrain requirements remain. Moves and PP are never changed.

Three-game suite component. Current automated checks use gen1recomp 0.3.39; complete gameplay validation remains deferred. Older validation reports describe their original FRLG snapshots.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

START > QOL > HM FIELD KIT lists actions currently usable. Existing overworld Cut/Surf/Strength/Rock Smash/Waterfall checks use the same owned-HM fallback. Badge and terrain checks remain. Fly is reached through Dual Screen’s separate FLY shortcut, not the Field Kit menu. The compact Dual Screen FLY tile can launch the native Fly map with this kit’s owned-HM fallback. No moveslots are modified; using a field move retains its normal game effects.

Options are in this mod's manager entry. ENABLED turns its behavior off. Mods with tools share one START > QOL menu automatically; there is no required central package.

**Sweet Scent (0.2.4):** on **gen1recomp 0.3.42+**, use any non-egg party Pokémon without learning the move, owning an HM or earning a badge. Open **START → QOL → HM FIELD KIT → SWEET SCENT**, or use the existing compact Dual Screen tile. Stand on grass/cave terrain with land encounters or water with native water encounters. Availability is checked again on selection; busy states are blocked. The normal animation and native encounter rules run, with no changes to moves or PP. Disabling this component restores learned-move requirements. Older engines do not receive this extension. Dig and Teleport still need to be learned.

## Compatibility

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. Declares `engine_internals` because the public API lacks the necessary narrow extension point. Other mods replacing the same functions may conflict. Inactive wrappers fall through after the loader changes; restart fully after a load error. Online/arena play is outside this package's scope. No ROM, graphics, audio or extracted data included.

## Validation

See VALIDATION.md and the collection's tests/ for the ROM-free checks and the exact limitations. For standalone checking, use upstream `tools/modkit.py lint` and `validate` on this directory.

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![HM Field Kit details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_hm_field_kit-detail.png)

![HM Field Kit options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_hm_field_kit-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
## Start menu fix (0.1.2)

Without Scrollable Start Menu, more than nine entries now use a compact right-hand scrolling sidebar instead of a full-screen panel. Native selection and callbacks are preserved. Update both HM Field Kit and Dex Companion if installed, then restart the game. No configuration changes are required.

## Flash and cave lighting (0.2.0)

Use START > QOL > HM FIELD KIT > FLASH in a dark cave with HM05, the Boulder Badge and any non-egg party Pokémon. Flash no longer fails because of missing cave context in older engines. Normal badge and already-used checks remain.

In the mod manager options, toggle **FULL CAVE LIGHTING** to fully illuminate dark caves. Default: off. No HM, badge or compatible Pokémon is required for this display option. Turning it off (or disabling the mod) restores the current native darkness immediately. It does not change save data or Flash flags; using Flash normally still takes effect.

## Native actions and fishing (0.2.1)

The kit now builds complete native field context and opens the game's Party action flow. Cut checks the surrounding 3×3 grass at the same elevation; Waterfall checks the facing tile, direction and surfing state; Flash retains badge, cave and already-active checks. Owned HMs work with any non-egg party member without teaching moves.

**FISH** appears when facing fishable water with an owned rod. Choose Old, Good or Super Rod in the picker; the game’s Bag Use action starts normal fishing. Fishing into a waterfall is rejected. Move and rod availability is checked again when selected.

Update Gen3DualScreen to **0.3.19** for the same owned-HM support in its compact field-action tiles. HM Field Kit is now supplied through the QoL Suite.

## 0.2.2 Strength eligibility

The shortcut requires facing a pushable boulder and native Strength eligibility; already-active Strength is not offered. No shortcut bindings changed.

HM availability checks read live bag slots without rebuilding or sorting the bag. This avoids overworld stalls when Gen3DualScreen refreshes its field tools, especially with Emerald's larger HM pocket. Battle Pyramid bag restrictions remain in effect.
