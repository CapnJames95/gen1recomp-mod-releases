> **0.4.16 — Hold L for shiny:** With Shiny Hunter 0.3.4+ enabled, hold the mapped L shoulder button while tapping a Wild Pokémon encounter to request one shiny encounter. Saved odds stay unchanged.

> **0.4.15 — Wild Pokémon shiny-odds integration:** With Shiny Hunter 0.3.3+ loaded, enable **Dual Screen odds** in its menu to apply the selected odds to Wild Pokémon button/tile encounters. The toggle defaults to OFF. Species, level, encounter availability and normal battle/capture flow remain unchanged.

# Gen3DualScreen 0.4.16

## Changes since public v0.4.15

Support for **all five Gen 3 games — Ruby, Sapphire, Emerald, FireRed and LeafGreen — is here**. Adds Ruby/Sapphire PokéNav, bag, summary and PC integration. Fixes text, Fly, fishing and touch controls; integrates Shiny Hunter odds and the hold-L shiny shortcut.


<!-- RS-COMPATIBILITY -->
## Ruby and Sapphire compatibility

Ruby and Sapphire now use native PokéNav, summary, bag and PC paths, with edition-specific route objectives and bike controls. Bag touch actions follow the native column order; move-selection touch controls preserve empty move slots and Cancel. The opening caption covers R / S / E / FR / LG. Native-state tests passed; rendered layouts and hardware touch still need checking.

Validated with gen1recomp **0.3.56 (Mac) / 0.3.57 (Android)**. Automated checks do not replace exhaustive gameplay testing.
<!-- /RS-COMPATIBILITY -->

Companion-screen mod for **Ruby, Sapphire, Emerald, FireRed and LeafGreen**; use gen1recomp **0.3.56+**. Built on **Kanto Gear 3.4.0**, with a shared visual style and integrations for this mod collection. The internal ID remains `frlg_dual_screen` for upgrades. Do not enable the original Kanto Gear alongside this mod.

## New in 0.4.14

Emerald’s **POKENAV** tile opens the native PokéNav rather than the themed map. It respects PokéNav acquisition and busy-state restrictions. FR/LG retain MAP. Emerald Town Map, Fly map and PokéNav use an isolated 240×160 viewport below the companion toolbar; the upper screen stays black while these native navigation screens own the display. QoL Suite 0.3.8 removes Start-menu resizing and moving.

![Emerald PokéNav](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-pokenav.png)

![Emerald Town Map](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-town-map.png)

## Current features

- Four-page Home arrangement copied from the Thor's Emerald setup and applied across all three games. Existing saves adopt it once; subsequent edits persist. Previous durable Home state is retained in `home/before-thor-preset`. Game-specific unavailable tiles are omitted without shifting other tiles.
- All 31 option defaults match the captured Thor configuration, including Quick Swap enabled. Existing explicit options are preserved. **Reset Home** restores layout and visibility; **Reset Options** restores option defaults.
- Long-press to arrange Home tiles. Three compact text/action rows fit beside one regular widget. Tile visibility saves immediately and retains the tile's position.
- Individual **Old Rod, Good Rod, Super Rod, Use Bike** and bike-swap tiles. Swap displays the current bike's name and changes an owned Mach/Acro Bike immediately in Emerald when safe.
- Compact **Fly, Dig, Flash, Sweet Scent and Soft-Boiled** actions dim when unavailable. Fly opens the native destination map. Squirt Bottle and Headbutt shortcuts are hidden. The general Field widget and duplicate native Teleport tile are removed; the Teleport mod shortcut remains.
- Home launchers for LegalMon, Event Distributions, Shiny Hunter, Auto Breeder, Encounter Tour, Encounter Reset and enabled suite tools, including Hoenn Tools in Emerald.
- Paged mod-tool menus use **PREV PAGE / NEXT PAGE / BACK**. Back sends the menu's normal Back input. Editors and progress/preview screens retain their context-specific controls.
- Wild Pokémon view with Uncaught/All/Caught filters; tap the filter text to change it. Encounter spawning uses native encounter data and rejects unsafe/busy states.
- Party, Summary, map, bag, trainer, Pokédex, shop and battle views, plus native-screen fallback for specialised menus. Emerald includes Contest Moves and owned/wild Summary IV/EV support with the suite's Summary IVs feature.
- Live QoL switches and companion tools share the collection's visual style. Mod Actions is available from supported Party/Map contexts; closing a Party overlay clears its sprite presentation.
- Battle effectiveness uses native type calculations with move-type and immunity checks. A ball picker provides native item artwork and configurable bindings; Capture Help uses the companion during ordinary wild battle commands when enabled.

**Sweet Scent:** the native encounter-start bug is fixed in [gen1recomp 0.3.42](https://github.com/bryanthaboi/gen1recomp/releases/tag/v0.3.42), closing [upstream #2601](https://github.com/bryanthaboi/gen1recomp/issues/2601). Isolated Safe Mode retests pass for FireRed, LeafGreen and Emerald. With **QoL Suite 0.3.9 / HM Field Kit 0.2.4**, the existing Sweet Scent tile uses any non-egg party member without teaching the move. The tile dims off encounter terrain. Engine 0.3.42+ is required; disabling Field Kit restores the native learned-move requirement. No engine workaround is included. [Test scope](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/SWEET-SCENT-RETEST.md).

## Install and use

1. Import the current [ZIP](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-dual-screen-0.4.14.zip), enable Gen3DualScreen for the desired game, then restart.
2. Update the other collection packages and **QoL Suite 0.3.9** together. Disable older standalone QoL components to avoid duplicate hooks.
3. Open a save. Home appears on the companion display, or in the selected desktop layout. The same arrangement is used for all three games; Hoenn Tools is Hoenn-only, with game-specific facilities.
4. Open **Options → Display** for Separate Window/Screen or combined layouts, including Side by Side. Device detection and output settings determine where the companion appears.
5. Use **Options → Home Tiles** to show/hide tiles, or long-press Home to rearrange them. Unavailable direct actions are dimmed and do not fall back to the Tools page.

All other collection mods work without Gen3DualScreen. Their native Start/QoL menus remain available. The companion provides a common presentation and shortcuts, not a requirement for Pokémon generation, breeding, events or services.

## Controls and display options

- Touch rows to select them; release activates a valid tap. Dragged, cancelled or mismatched-finger touches do not confirm actions.
- Keyboard **F8** opens the uncaught encounter view by default; its controller binding defaults OFF. Set **Uncaught Key / Button / Area** under Options → Controls.
- Ball picker defaults: **F7** keyboard / **Y** controller. Bindings are configurable.
- Quick Swap (**F6**) defaults ON. Trigger Tabs defaults OFF; keyboard layout defaults QWERTY; haptics defaults OFF.
- Separate display is the default. Combined mode offers Auto, Stacked, Side by Side and Overlay, with primary view, secondary size, safe-area and overlay controls.
- **Hide Main Start** defaults ON only when a ready separate companion display is active. Combined/fullscreen modes and a missing companion retain the native Start menu.
- Modal editors pause gameplay. Supported live editors explicitly yield to the overworld; battles, transitions, scripts and busy automation restrict conflicting actions.

## Compatibility and limits

**AYN Thor is the only physical dual-screen device tested.** Other dual-screen devices are untested. Desktop controls/layouts are implemented; fuller interactive Mac/Windows validation remains outstanding. Ruby and Sapphire are not supported.

All eight current collection packages support the three target games. The suite has 32 components, 31 applicable per game: Hoenn Tools is Hoenn-only, with game-specific facilities, Disable L/R Help is FRLG-only. HM Field Kit requires an owned HM plus normal badge/terrain eligibility, with any non-egg party member; it does not teach moves or change PP.

Automated checks cover imported native data, UI controls, layout migration, menu Back handling and collection integration. They use isolated sessions and do not establish an exhaustive playthrough or compatibility with unrelated creators' mods. See [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md) and [historical validation reports](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg_dual_screen/VALIDATION.md).

## Current previews

These are current native-renderer previews with synthetic state, not new hardware gameplay captures. Empty party/inventory and Unknown Area labels belong to the fixture. See [screenshot provenance](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/SCREENSHOTS.md).

![Shared Home layout, Emerald pages 1–4](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-home.png)

![Shared Home layout, FireRed pages 1–4](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/firered-home.png)

![Current mod-tool page and Back footer](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-legalmon.png)

![Current startup in light and dark](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg-dual-screen/startup.png)

![Compact actions and owned/wild Emerald IV tables](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg-dual-screen/portable-summary.png)

## Credits and differences from Kanto Gear

[Kanto Gear](https://github.com/AverageConsumer/kanto-gear), by AverageConsumer, supplies the **3.4.0 foundation**. Gen3DualScreen adds collection-aware launchers and editor ownership, suite switches, three-game adapters, native menu/context integrations, compact rod/bike/field actions, tile visibility and the shared Thor Home preset. Its version number is independent of Kanto Gear's.

The inherited Gen1/Gen2-oriented Squirt Bottle and Headbutt shortcuts are hidden for this three-game collection. The general Field widget and virtual controller deck are removed. The [collection README](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/README.md#differences-from-kanto-gear) gives the comparison; retained historical development details are in Git history and validation documents.
