# QoL Suite 0.3.11

## Changes since public v0.3.10

Support for **all five Gen 3 games — Ruby, Sapphire, Emerald, FireRed and LeafGreen — is here**. Updates all 32 components for game-appropriate five-game support. Fixes daycare deposits, native text, bag touch actions, bike swapping and Repel handling; Hoenn tools use Ruby/Sapphire’s native facilities.


<!-- RS-COMPATIBILITY -->
## Ruby and Sapphire compatibility

All 32 components now recognize Ruby and Sapphire where applicable. Native HM shortcuts require the owned HM and normal badge permissions, but do not require a compatible party species. Hoenn tools use Trainer’s Eyes, Battle Tower records and native Level 50/100 party-entry checks in Ruby/Sapphire; Emerald-only facilities and weather-cave features stay restricted to Emerald. Teleport offers 16 native Ruby/Sapphire Fly destinations with progression locks enabled by default. Route 117 daycare, Pokémon services and summary IV/EV integration use native Ruby/Sapphire paths.

Validated with gen1recomp **0.3.56 (Mac) / 0.3.57 (Android)**. Automated checks do not replace exhaustive gameplay testing.
<!-- /RS-COMPATIBILITY -->

**New in 0.3.9:** HM Field Kit adds untaught Sweet Scent on engine **0.3.42+**, using any non-egg party member and native encounter generation. Available from the Field Kit menu and the existing Dual Screen tile, only on encounter terrain. Moves/PP are unchanged.

**New in 0.3.8:** Removed the Start-menu size/position editor and saved resizing/moving. Automatic sizing, scrolling, folders and ordering remain.

**New in 0.3.7:** HM Field Kit accepts any non-egg party Pokémon regardless of learnset, while requiring the actual HM in the bag, the correct badge and valid field conditions. No moves are taught or changed.

**New in 0.3.6:** Berry Garden groups neighbouring trees into 27 unique patches across 16 Hoenn maps. All 88 planting spots are included, even empty/unseen soil. Each patch has one teleport and individual tree information. Mirage Island still requires a safe landing when present.

**New in 0.3.5:** Emerald shop owned counts appear above the item icon and follow the scrolled selection. The Emerald Move Deleter can be cancelled without deleting a move.


**Previously in 0.3.3:** Back returns one page at a time through Dex Companion, HM Field Kit and Hoenn Tools, retaining cursors and the original QoL/Start menus. Direct companion entry returns to gameplay. Successful field actions still dismiss the chain; unavailable actions return to the tool. Back input is consumed in services, teleport, healing, capture and daycare menus so it cannot also dismiss their parent.

**Previously in 0.3.2:** Emerald Summary IVs shows IV/EV values immediately for owned and inspected wild Pokémon, with A/B returning to native stats. Town Map Companion exposes location notes to Dual Screen’s Mod Actions in all three games. Teleport Unlock All defaults to OFF; explicitly saved choices are preserved.


0.2.1: Fly Teleport lists destinations first, then the inline Unlock All toggle, followed by Help and Close.

**32 QoL components in one importable mod**, with individual on/off switches and their original options. Ruby, Sapphire, Emerald, FireRed and LeafGreen support; gen1recomp 0.3.56+ recommended. Each game shows 31 applicable tools: Disable L/R Help is FRLG-only and Hoenn Tools is Hoenn-only, with game-specific facilities. Gameplay-changing options such as reusable TMs and the wild inspector retain their existing defaults.

[Download the suite](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-qol-suite-0.3.11.zip) · [Validation and limitations](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/VALIDATION.md) · [Included components and source hashes](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/components.json)

## New in 0.3.0

- [Hoenn Tools](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/mods/frlg_qol_hoenn_tools/README.md) adds eight Emerald companions for Match Call, berries, the Frontier, Feebas, contests/Pokéblocks, bikes, daily events and secret bases. Open START → QOL → HOENN TOOLS or its Dual Screen tile.
- Emerald’s Fly-map service notes now display the selected destination’s native Fly eligibility.
- Game-specific wording and Scrollable Start Menu naming corrected.
- Gameplay validation is deferred by request; Thor performance is reported excellent.

## New in 0.2.0

- Emerald Quick Field Actions keeps native Cut, Rock Smash, Strength, Surf and Waterfall scripts and effects, and adds A-button Dive and surfacing. Badge, terrain and compatible-party requirements remain; HM Field Kit supports owned untaught HMs. Flash remains available only where native Flash has an effect.
- Route 117 Day Care, 17 Hoenn Fly destinations, Lilycove item shops and vending machines, and native Hoenn remote services replace Kanto-specific choices. Battle Frontier challenges block remote healing, travel and daycare changes.
- The party Move Reminder opens Emerald's own screen and charges one Heart Scale after a successful lesson. The separate Services reminder remains free.
- Summary IVs uses an A-button IV/EV panel on Emerald's Skills page to avoid overlapping native stats. FRLG keeps its inline layout.
- Hoenn map notes/key-item guidance and Match Call readiness replace Kanto notes and VS Seeker information. Emerald has no Disable L/R Help feature because it has no FRLG Help system.
- Quick Heal Party and Capture Assistant now activate in Emerald. Existing settings and component IDs are retained.

The linked ZIP contains this version. See [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md). Automated tests do not establish manual device compatibility.

## New in 0.1.4

**Quick Field Actions** replaces Auto Surf and adds A-button Cut, Strength, Rock Smash and Waterfall alongside Surf. Face a suitable target and press A to skip confirmation and used-move text. Waterfall requires surfing and facing up; Strength activates boulder pushing. Native eligibility, animations and HM Field Kit support remain in place. Existing Auto Surf settings are preserved.

## Install or migrate

1. Import the suite ZIP through the launcher's mod importer.
2. **Disable the standalone component mods before enabling the suite**, then restart. Older installed folders can be retained disabled or removed. The suite declares explicit conflicts so two copies cannot run together. The seven other mods, including Dual Screen, remain separate.
3. If using Dual Screen, update it to **0.3.21 or newer**. Older versions do not recognise bundled feature IDs correctly.
4. Open **START → QOL → QOL SETTINGS**. Press **A** to toggle the selected feature, **SELECT** for its original options, and **Left/Right** to page. In a feature's options, A or Left/Right changes the value; B returns. START closes the menu.

Dual Screen's **Live QoL** page also lists all applicable switches. Native QOL SETTINGS routes to the lower screen, with tappable rows and an OPTIONS footer. Quick Heal and Capture Help retain their Home tiles. Existing QOL tools and other native shortcuts remain where the individual features put them.

Settings use each original mod's existing option keys. No destructive migration is performed. Saved feature settings, keyboard/controller bindings and Scrollable Start Menu layout remain readable by the standalone versions for compatibility with existing installations. Launcher package enablement is separate: disabling old packages to migrate does not disable their corresponding suite features. Previously unset feature options use their standalone defaults.

The suite's manager ENABLED switch gates the whole package. Individual switches do not erase settings. Disabling a feature stops its behaviour; it does not undo earlier gameplay changes made with it. This package is a consolidation, not a new legality guarantee or a preset for faithful play.

## Compatibility

The package embeds the canonical runtime files from the 24 `qol/mods` modules plus Disable L/R Help, Scrollable Start Menu, Summary IVs, Quick Heal Party, Capture Assistant, Pokemon Services, Fly Teleport and Day Care Viewer. There is exactly one installable root manifest. Components initialize once at `game.ready`, using the engine's original per-ID option and storage APIs. They do not appear as 32 extra installed mods.

Dual Screen 0.3.21 resolves active bundled features through an explicit compatibility API. This preserves Home availability, party/map context actions, HM field checks, shared ball-menu ownership, native IV Summary routing and hold-to-fast-forward exports. Component failures are reported in the host's error feed and the settings menu; failed components remain inactive.

The suite uses `engine_internals`, including the loader's API factory, and is therefore engine-version-sensitive. See validation for the exact tested engine revision. No ROM, imported cache, save or generated Pokémon is included.

## Shortcuts

Open **START → QOL → QOL SHORTCUTS**. Choose an action to see where it works and edit its bindings with A or Left/Right. Defaults are preserved. Settings persist through the host's normal option storage.

The page covers Hold Fast Forward, Ball Shortcut, Wild Inspector, Party Held Items, Party Nickname, Move Reminder, Town Map Services, Expanded Summary, inspector IV/EV switching and Capture Help. Tools with no dedicated shortcut still use their existing menu entries.

For previously fixed shortcuts, **GAME BUTTON** selects a logical GBA button, using your existing keyboard/controller mapping; OFF disables that route. **EXTRA KEY** and **EXTRA PAD** add direct shortcuts, including L2/R2 triggers. These bindings apply only in the action's valid context. Ordinary menu navigation, confirmation and back controls stay mapped by the game. Capture Help's R/B/START closing controls remain unchanged inside its panel.

Existing configurable tools use their original binding choices. If two actions share a binding in the same context, the first eligible handler wins; choose distinct keys for overlapping battle or party actions. Hold Fast Forward remains a held control and can overlap other inputs.

![Shortcut actions](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-suite-shortcuts.png)

![Shortcut settings with context](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-suite-shortcut-context.png)

## 0.1.1 fixes

Settings now live inside QOL. The bundled Scrollable Start Menu fixes double application of the native scroll offset, keeping the selected row and cursor aligned when moving or wrapping through a long menu. The standalone Scrollable Start package contains the same fix. Capture Help's instructions now acknowledge configurable launch bindings.

Rebuild using `python3 tools/build-qol-suite.py`; verify byte identity and the archive with `python3 tools/build-qol-suite.py --check` from the collection root. Standalone sources remain canonical; do not edit the generated `components/` tree directly.

## Menu previews

Native draw traces using the installed game fonts and synthetic sessions; these are not physical-device screenshots.

![QoL feature toggles](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-suite-menu.png)

![Original feature options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/qol-suite-options.png)

## 0.1.2 navigation fix

B in QOL returns to the existing Start menu, keeping its cursor, scroll position and organized layout. B from Settings or Shortcuts returns to QOL. START closes this entire menu chain. Existing field-tool launch behaviour is preserved.

## 0.1.3 additions

Includes Pokemon Services, Fly Teleport and Day Care Viewer with their original START entries (SERVICES, TELEPORT and DAY CARE) and Dual Screen Home tiles. All three have individual switches under QOL SETTINGS. These tools use normal menu controls rather than dedicated launch hotkeys. Day Care Viewer receives a suite enable switch; all component runtime files remain identical to their standalone sources. Fly Teleport retains its default progression locks and optional ALL DESTINATIONS UNLOCKED setting; it still bypasses the Fly move and badge requirements as before. Native service costs and Day Care restrictions remain unchanged. Disable standalone copies before enabling this suite.

## Distribution

The suite is the only QoL download. The standalone component ZIPs have been removed, including Pokemon Services, Fly Teleport and Day Care Viewer. Canonical component source folders and historical tests remain in the repository solely to rebuild and verify the suite.

## 0.1.5 field actions

HM Field Kit offers Strength only while facing a pushable boulder, with native badge/party eligibility and Strength not already active.

## 0.1.6 menu and ball ownership

Back consumes its input edge before returning to the parent menu. When Dual Screen is installed, the suite Ball Shortcut is inactive and hidden from settings, Live QoL and shortcut pages. Its saved preferences are retained and restored if Dual Screen is removed. Other key bindings are unchanged.

## 0.1.7 dedicated shortcuts

Fast Forward defaults to F9 (keyboard) and L3 (controller). Dual Screen screen swap uses F6 only; Y is reserved for its ball picker. Overlay visibility defaults to R3 in overlay mode. Ball picker remains F7/Y, Capture Help remains R, and Trigger Tabs remains off. Existing saved overrides are preserved unless explicitly changed.

Regression checks cover F9/L3 defaults, Right Ctrl falling through, Y not swapping, F6 edge handling and R3 overlay activation.

[Current screenshots for every included component](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/RELEASE-SCREENSHOTS.md).
