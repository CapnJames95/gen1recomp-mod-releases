# Scrollable Start Menu 0.3.1

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

A FireRed / LeafGreen / Emerald component for gen1recomp, mod API 2.

[QoL Suite download](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-qol-suite-0.3.9.zip).
Import the suite through **MODS → Import mod .zip**, enable it for your edition and restart. The Scrollable Start Menu component is enabled by default.

## Current menu layout

Manual resize and move controls have been removed in 0.3.1. The native popup uses automatic sizing and its normal position; previously saved size/position values are ignored. Saved folders and ordering are retained.

## Scrolling

The native Start menu grows vertically to fit its entries. The visible row count respects the edition’s native limit, spacing and available 240×160 canvas. Larger menus scroll as Up/Down moves the selection. Wrapping from the first entry to the last (or back) scrolls to that entry. A scrollbar indicates your position. The panel also widens for mod labels, up to the available screen width. Enlarging the desktop window scales the game canvas; it does not add logical menu rows.

## Folders and sorting

Open **START → ORGANIZE MENU**:

- **NEW FOLDER:** name a folder with the native controller keyboard (up to 12 characters). Select OK to finish; finishing with an empty name cancels creation. B deletes a character; Start jumps to OK.
- **ORDER MAIN MENU:** highlight an entry with Up/Down, press **A to pick it up**, use **Up/Down to move it**, then press **A to place and save**. **B cancels** the move. The title shows MOVING while an item is picked up. The same controls apply to folder contents. **SORT A-Z** alphabetizes entries and folders; use MOVE MOD ENTRIES or EDIT FOLDERS for destination and folder settings.
- **MOVE MOD ENTRIES:** choose a mod shortcut, then a folder or **MAIN MENU**. A shared shortcut such as QOL moves as a single entry.
- **EDIT FOLDERS:** rename a folder, reorder its contents, or delete it. Deletion asks for confirmation and returns its entries to the main menu.
- **RESET LAYOUT:** confirm to remove folders and restore the host's entry order.
- **DONE:** return to Start. B goes back one editor screen; Start leaves the editor.

Folders appear as **+ NAME**. A opens one; B/Start or **BACK TO MAIN** returns to the main menu. Folder contents use the same automatic height and scrolling. **ORGANIZE MENU** remains available at the bottom of the main menu and each folder.

Core game entries (Pokédex, Pokémon, Bag, trainer, Save, Option, Mods and Exit) can be reordered but stay at the top level. Folders have one level; nested folders are not supported. Only shortcuts supplied by currently enabled mods can be moved. Disabling a mod hides its shortcut while retaining its saved folder assignment; new shortcuts appear at the top level. Entries are identified by their host ID, falling back to label and occurrence when a mod supplies no ID. An ID/label change in another mod can therefore appear as a new entry.

Reordering saves when you place the item with A; Start discards an unfinished move and exits the editor. Other changes save immediately in this mod's private storage, separately for each edition and playthrough. A failed write displays an error and leaves the previous layout in effect. This does not rewrite Pokémon, inventory, or story progress. The **ENABLED** setting disables both organization and the scrolling fix.

Native callbacks, wraparound, exit confirmation and Safari statistics remain supported. Safari, link and Union Room menus retain their native entry layout and do not offer the organizer. Designed to coexist with the collection's QoL menu wrappers regardless of startup order. Gen3DualScreen has its own touch layout; shortcuts it removes from the native Start menu cannot be organized here. Other third-party mods that completely replace the renderer may conflict.

## Validation

Run from this directory:

```sh
lua tests/runtime.lua /absolute/path/to/gen1recomp
lua tests/organizer.lua /absolute/path/to/gen1recomp
```

Passed with LuaJIT against local host `fab224458f9d5af79a82b5ff5338347ef74c0189` and with Lua 5.4 against a second local engine snapshot, for both edition settings:

- Existing native-render tests: 1/7/8/9/10/14/40 entries, selection and callbacks, bounds, wraparound, confirmation, Safari, renderer load order, disable/teardown and error restoration.
- Organizer interaction tests: folder creation/open/back/rename/deletion; manual and A-Z sorting; moving entries; original callbacks; reopening; temporarily unavailable mods; playthrough isolation; reset confirmation; failed reads/writes; disabling; Safari exclusion; 25-entry folder scrolling and wraparound.
- Host SDK loading and native-font/frame render fixtures. Screenshots use synthetic settings and entries, with no player storage writes.

Live gameplay and physical-device testing remain unverified. Requires `engine_internals`; future host changes may require an update. Created with AI assistance; unofficial and experimental.

## Screenshots

Native render fixtures: organized main menu, folder, organizer and ordering controls. These are isolated UI examples, not gameplay captures.

Historical preview (older build): [Start menu organizer](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/start-organizer-preview.png).

## Changes

**0.2.1:** A picks up an entry, Up/Down moves it, A places/saves it, and B cancels. Movement previews do not save until placement.

**0.2.0:** saved ordering, A-Z sort, named folders, moving mod entries, renaming/deleting folders and reset controls.

**0.1.1:** advertises active Start-menu renderer ownership so QoL helpers delegate rather than drawing a second paged menu.

**0.2.2:** respects Gen3DualScreen 0.3.14’s **Display → HIDE MAIN START** setting, including suppressing the scrollbar. The setting defaults ON only taking effect when a separate companion display is detected and ready.

## 0.2.3 scrolling fix

The renderer clears the native scroll offset while drawing its already-scrolled window and restores it afterwards. Its row capacity also respects the host renderer limit. This fixes missing rows/cursor jumps near the ends of long menus. Both-edition native HUD tests now walk the complete menu in both directions and wrap at the ends.
