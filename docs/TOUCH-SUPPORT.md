# Touchscreen support with Gen3DualScreen

## Current controls — Gen3DualScreen 0.4.14

Paged collection tools use **PREV PAGE / NEXT PAGE / BACK**; Back returns through the tool’s normal parent chain. Specialised native screens retain the Actions palette for directional input, Choose and Back. In Emerald, the Home **POKENAV** tile opens native PokéNav after acquisition. Native Town Map **MOD ACTIONS** opens location/service information. The native map occupies its own viewport below the toolbar, while the upper screen is black. Start-menu organization and scrolling remain; resize/move controls have been removed.

## Earlier touch-support evidence

> **Historical report.** Version numbers and test results below describe their recorded development snapshots. Current versions and installation status are in [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md); screenshot freshness is recorded in [the image audit](SCREENSHOTS.md).


The eight current packages, including all 31 bundled QoL features, have a touch access path with **Gen3DualScreen 0.3.21**. Install the [Dual Screen update](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-dual-screen-0.4.14.zip) and [QoL Suite download](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-qol-suite-0.3.9.zip), or the [updated manual-install bundle](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/gen1recomp-all-mods-manual-install.zip). Restart after replacing installed packages. This work targets the Dual Screen setup requested, not independent touch controls in every standalone package.

## Touch controls

- Tap visible menu rows to select. Swipe vertically or use **PREV PAGE / NEXT PAGE** for long lists. The alphabetic and numeric keyboards follow their displayed keys.
- **ACTIONS** exposes Up/Down, Left/Right, Choose, Back, L, R, Select and Start for specialised pages and native fallback screens. For example, use Choose to pause/resume a search, R to inspect Auto Breeder parents, or Select for LegalMon's best result. The normal confirmations remain in place.
- **MOD ACTIONS** on Party opens held items, renaming and the mushroom move reminder. Native summary information and Town Map services use **ACTIONS → SELECT**. The companion Map's MOD ACTIONS button opens the native Town Map.
- In **LIVE QOL SETTINGS**, enable Hold Fast Forward and hold **HOLD TO FAST FORWARD**. Release, slide off, leave the page or lose focus to stop. Speed locks and session boundaries still apply.
- Native menus, including the Scrollable Start Menu organizer, retain the Actions fallback. Its Up/Down and Choose buttons can select and move organizer entries.

A row activates on release, not initial contact. Dragging off a row, a second finger, cancellation, changing screens or releasing over another row cannot confirm the original action. These are menu controls; no gameplay controller deck was added.

## Coverage

Background QoL mods do not need an extra action button. Their enabled setting is touch-accessible in LIVE QOL SETTINGS or the native mod manager; any other options use the native mod manager. Their underlying game menus retain Dual Screen's native touch adapters.

| Mod | Touch access |
| --- | --- |
| LegalMon | Home tile → row taps, paging, Back and Actions. |
| Event Distributions | Home tile → row taps, paging, Back and Actions. |
| Shiny Hunter | Home tile → row taps, paging, Back and Actions. |
| Auto Breeder | Home tile → row taps, paging, Back and Actions. |
| Encounter Tour | Home tile → row taps, paging, Back and Actions. |
| Gen3DualScreen | Existing Home, settings, map, party, bag, battle and native-menu touch adapters; expanded mod panels. |
| Day Care Viewer | Home tile → row taps, paging, Back and Actions. |
| Encounter Reset | Home tile → row taps, paging, Back and Actions. |
| FRLG Scrollable Start Menu | Native Start list; organizer uses Actions → Up/Down/Choose/Back. |
| Auto Surf | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Sorted Bag | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Battle Ball Shortcut | Existing companion ball selection; native ball menu supports row taps and paging. |
| Battle Bar Speed | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Held Berry Replacement | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Dex Companion | Native Start → QOL → tool; tap rows or use Actions. |
| Faster Center Healing | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| HM Field Kit | Native Start → QOL → tool; tap rows or use Actions. |
| Hold Fast Forward | LIVE QOL SETTINGS → hold-to-fast-forward button. |
| Fast / Instant Text | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Key Item Help | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Town Map Companion | Native Town Map → Actions → Select. |
| Party Held Items | Party → MOD ACTIONS → corresponding native action. |
| Party Nickname | Party → MOD ACTIONS → corresponding native action. |
| Party Move Reminder | Party → MOD ACTIONS → corresponding native action. |
| Quicker Save Confirmation | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Quiet EXP | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Repel Reuse Prompt | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Reusable TMs | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Running From Start | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Shop Owned Count | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Expanded Summary Info | Native summary → Actions → Select. |
| VS Seeker Readiness | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Quick Heal Party | Home tile → row taps, paging, Back and Actions. |
| Capture Assistant | Home tile → row taps, paging, Back and Actions. |
| Pokemon Services | Home tile → row taps, paging, Back and Actions. |
| Summary IVs | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Disable L/R Help | Automatic/native-menu behaviour; options through the touch mod manager or LIVE QOL SETTINGS. |
| Fly Teleport | Home tile → row taps, paging, Back and Actions. |

## Verification

- **595/595 collection and touch checks per edition**, using actual mod-loader instances and synthetic test sessions. This includes all 11 custom tool panels, every Live QoL toggle, numeric and alphabetic key hitboxes, held-item/nickname/reminder actions, summary/map Select actions, cancellation and fast-forward release/focus handling.
- Native pointer, runtime, menu-control, route, progress and online regressions pass on FireRed and LeafGreen. The native control suite passes 1,404 checks per edition.
- The independent Hold Fast Forward suite passes 14 assertions per edition, including physical controls, focus/speed locks, touch hold/release and disabled state.
- A real LÖVE renderer was used to inspect the menu layouts shown below. No physical touchscreen device was available for this run.

Tests use engine commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf` and the user's existing imported caches. No player saves were loaded or changed.

Touch menu layout checks

Touch suite · Runner · Results

The two updated packages pass source-parity and archive-integrity checks, and the rebuilt bundle matches all 38 individual ZIPs. A separate collection-wide source audit observed Fly Teleport being updated concurrently (its new source and download links had not yet been packaged); this task did not overwrite that work. See the audit snapshot.
