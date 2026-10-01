# Fly Teleport 0.2.2 — Emerald / FireRed / LeafGreen

Current companion preview (synthetic Emerald session; Dual Screen is optional):

![Current fly-teleport menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-fly-teleport.png)


**Emerald support (QoL Suite 0.3.7):** Lists 17 native Hoenn Fly destinations instead of FRLG's 20, with the edition's visited flags and optional all-unlocked mode. All 17 map landing points pass collision and native-warp tests. Teleports land on foot, clearing underwater and bicycle state; active Frontier challenges block travel. Manual device testing remains pending.


**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

**START → TELEPORT** lists every native Fly destination in the collection's usual FRLG menu: blue header, striped background, six scrolling rows and the player's selected window frame.

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

Select a destination, then **Teleport now**. Confirmation starts on **Cancel**. Up/Down scrolls, Left/Right skips five rows, A selects, B/L goes back and START closes.

## Destinations

Pallet Town, Viridian City, Pewter City, Cerulean City, Lavender Town, Vermilion City, Celadon City, Fuchsia City, Cinnabar Island, Indigo Plateau, Saffron City, Route 4 Pokémon Center, Route 10 Pokémon Center, and One through Seven Island: **20 destinations**.

**Game progression is the default.** Destinations unlock using the same visited flags as the native Fly map. Locked destinations remain listed with `[LOCKED]`; choosing one explains that you must visit it during normal play. Existing saves immediately use their existing progress.

After the final destination, the menu shows **Unlock All: OFF / ON**. Press A or tap it to switch immediately without opening another page. **OFF** follows game progression; **ON** includes every destination. Alternatively, change **UNLOCK ALL** in the mod manager. The setting is saved through the normal options system; switching modes never sets or clears game progress flags. All-unlocked mode includes unvisited destinations.

Neither mode requires a Pokémon with Fly, a badge or ferry ticket to perform the teleport. Progression mode checks destination unlocks, not the ability to use the Fly move. Normal arrival scripts still run. The mod does not grant badges or tickets. Save normally to keep your new position.

Coordinates come from the active edition's imported Fly data. Travel uses the native map warp and lands on foot facing down. Battles, dialogue, movement, fades, linked activities and Safari games block travel; missing maps or obstructed landing points report an error. Confirmation rechecks the active session and destination.

Requires Mod API 2, `engine_internals` and Gen1Recomp >=0.3.21 <0.4.0. Tested against engine commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`; that older validation is historical. Current automated tests use 0.3.39; Thor has had limited smoke checks, not complete gameplay validation. No ROM, imported game data or player saves are distributed. See [validation](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/fly-teleport/VALIDATION.md).

## Screenshots

Native draw traces from synthetic sessions, not live play captures.

Historical preview (older build): [Fly destinations](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/fly-teleport/destinations-firered.png).
Historical preview (older build): [Sevii destinations](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/fly-teleport/sevii-firered.png).
Historical preview (older build): [Teleport confirmation](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/fly-teleport/confirm-firered.png).

Based on the Pokemon Gen 1 Recompilation Project by BOIS CLUB GAMES, LLC. Menu and travel conventions follow the collection's Quick Heal Party and Day Care Viewer mods.
