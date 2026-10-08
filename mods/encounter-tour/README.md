# Encounter Tour 0.3.2

## Changes since public v0.3.1

Support for **all five Gen 3 games — Ruby, Sapphire, Emerald, FireRed and LeafGreen — is here**. Adds Ruby/Sapphire destinations, starters, gifts, fossils and NPC trades, with native progression checks and prepared Groudon/Kyogre repeat encounters.


<!-- RS-COMPATIBILITY -->
## Ruby and Sapphire compatibility

Ruby and Sapphire have 26 native destinations covering legendary/static encounters, ordinary Kecleon encounters, Beldum, Wynaut, Castform, fossils, NPC trades and Southern Island. Story prerequisites apply. Steven’s first Kecleon scene, Fortree’s fleeing roadblock and the mascot story scenes are not replayed.

Validated with gen1recomp **0.3.56 (Mac) / 0.3.57 (Android)**. Automated checks do not replace exhaustive gameplay testing.
<!-- /RS-COMPATIBILITY -->

Current companion preview (synthetic Emerald session; Dual Screen is optional):

![Current encounter-tour menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-encounter_tour.png)


## Original starter repeats

In Encounter Reset, choose **Starters → Pokémon → Prepare repeat starter** after earning the Pokédex. Return to **Oak’s lab in FR/LG** or **Route 101 in Emerald**, then choose **Collect prepared starter** in the same menu with a free party slot. Each preparation permits one native level-5 gift; preparation persists when saved. Existing Pokémon and the original starter/rival/roamer selection are preserved. This does not replay the rescue or rival battle.

## Emerald support

0.3.0 supports FireRed, LeafGreen and Emerald on gen1recomp 0.3.39. Emerald has 31 entries.

- Existing legends, event-island encounters, static battles and Beldum remain supported.
- **New gifts:** Wynaut egg and Castform. Castform requires the Weather Institute quest to be completed; only its gift receipt is reset.
- **New NPC trades:** Seedot for Ralts, Plusle for Volbeat, Horsea for Bagon and Meowth for Skitty. Native scripts retain the offered-Pokémon requirement and fixed trade identity.
- **New fossils:** Lileep and Anorith. Reset supplies one missing Root/Claw Fossil, without replacing an unfinished revival. Hand it to the Devon scientist, leave and return to collect it.
- **New Johto starters:** Chikorita, Cyndaquil and Totodile. Reset reopens the **shared choice of one**, only after Birch's Johto reward has already been earned and collected. Original Hoenn starter and main story variables are not changed.

Native English Faraway Island Mew remains excluded because there was no official English Old Sea Map distribution. Encounter Tour includes the original Treecko/Torchic/Mudkip rescue destinations. Encounter Reset offers repeat starter gifts in all three games without rewinding the opening story, rival team or original starter choice.

Active Frontier challenges, battle transitions, dialogue and movement block travel/reset. Underwater return travel preserves the original map, position and underwater state. Changing the loaded save cancels old tour state and invalidates reset confirmations.

Imported-data tests verify all landing points, reward scripts, both Eon/roamer TV choices, native fossil handover/collection, all four trades and all three Johto reward scripts. These use synthetic saves; the new entries still need hardware gameplay testing.

Native menu previews below use synthetic fixture state, not live gameplay captures:

![Emerald NPC trade detail](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/encounter-tour-emerald-npc-trades-detail.png)

A standalone gen1recomp FireRed/LeafGreen teleport mod with the same native blue header, patterned background, window frames, bitmap font and Pokemon portrait layout as LegalMon. LegalMon is not required.

## Install

Import `encounter-tour-0.3.2.zip` in gen1recomp's mod manager, enable **Encounter Tour** for FireRed, LeafGreen or Emerald, and restart if requested. Open your save, then choose **START → ENCOUNTER TOUR**. Alternatively, extract the archive into a new `encounter_tour` folder in the game's mods directory, with `manifest.json` directly inside that folder.

Tested against an isolated copy of the installed **0.3.21** engine payload using both games' imported data. This uses engine internals; future releases may need an adapter update. It does not modify installed game files or live saves during installation. Pokemon art and UI assets load from your own imported game; the mod ZIP contains no ROM data.

## Controls and behaviour

- **Browse encounters:** select a category, Pokemon, then **Teleport here**.
- **Automatic tour → Start new automatic tour:** visits unresolved entries in catalogue order. You interact, choose dialogue, battle and catch normally. After a new matching Pokemon is acquired or the encounter's completion flag changes, it waits for the field to be idle for one second and moves onward.
- **Tour from here:** starts the sequence from your selected encounter.
- **Next / skip encounter:** moves onward when a prerequisite cannot be met or you wish to skip a stop. The tour cannot supply a fossil, coins, friendship, trade partner or Poke Flute for you.
- **START:** pauses the automatic tour before opening the normal game menu. Use Next to resume the route.
- **Return to start:** returns to the position before your first teleport in this session. It keeps your current party, PC, items and story progress; it is not a save rollback. A new return point is recorded on the next teleport after returning.
- **A** selects; **B / L / START** backs out of the mod menu. **Left / Right** jumps six rows. The game pauses while this menu is open.

The tour and return point are kept in memory and reset when the loaded session changes. Save normally to keep game progress. Pause Shiny Hunter or any other input/reset automation before using an automatic tour; simultaneous automation has not been verified.

## FireRed / LeafGreen fixed-encounter catalogue

40 menu entries across both versions, with 39 version-compatible entries per game. The other version's prize is marked `[X]` and cannot be selected for teleporting.

| Category | Entries |
|---|---|
| Starters | Bulbasaur, Charmander, Squirtle |
| Legendaries | Articuno, Zapdos, Moltres, Mewtwo |
| Event islands | Lugia, Ho-Oh, Deoxys |
| Static battles | Route 12 Snorlax, Route 16 Snorlax, both Power Plant Electrodes, Lostelle's Hypno, Marowak ghost |
| Gifts and eggs | Eevee, Lapras, Hitmonlee, Hitmonchan, Magikarp purchase, Togepi egg |
| Fossils | Omanyte, Kabuto, Aerodactyl |
| Game Corner | Abra, Clefairy, Dratini, Scyther (FR), Pinsir (LG), Porygon |
| NPC trades | Mr. Mime, Jynx, Nidoran, Farfetch'd, Nidorina/Nidorino, Lickitung, Electrode, Tangela, Seel |

The original story and acquisition scripts remain in control. Oak must offer a starter; only one starter and one Dojo prize can be claimed normally. Claimed gifts or resolved battles are not reset. `[DONE]` means the original completion flag is set, which may indicate defeat or a mutually exclusive choice rather than capture. You can still visit a resolved location individually.

**Event islands:** teleports bypass ferry/ticket access. Deoxys still requires the triangle puzzle. For Ho-Oh, walk one tile up from the landing point. Marowak's ghost is not catchable: walk one tile down from its landing point to trigger the story encounter. The menu includes the required interaction notes.

**No fictional destinations:** Raikou, Entei and Suicune roam rather than occupying fixed tiles. Mew, Celebi, Jirachi, external distribution Pokemon, event eggs and GameCube gifts have no native FRLG map encounter to teleport to. These are explained under **Other special Pokemon**; use the separate Event Distributor/LegalMon tools for external origins. Normal wild encounters, fishing, Surf, Rock Smash, Safari, Unown and breeding eggs are not individual static encounters.

## Validation and limits

- 25 controller checks passed: progression, completion gating, busy-field delay, pause, skip, version filtering, return point and session isolation.
- Both FireRed and LeafGreen passed all 40 landing validations and 40 real engine map loads, plus return, position/party/money preservation, blocked movement, version, flag, gift-egg and native menu/input tests.
- Both games passed native Zapdos interaction from the computed landing point through the original script into battle, and START-before-teleport pause checks.
- Landing validation rejects walls, water, ledges, occupied cells, map warps and coordinate-trigger tiles. Alternate adjacent tiles are used for Route 16 Snorlax and Electrode 1.
- Native menu draw traces were rendered and visually inspected. These are UI previews, not live gameplay screenshots.
- Mod manifest validation and ROM-content lint passed.

Map-load tests isolate each location by halting prior story setup in the test fixture. The shipped mod never halts scripts: it refuses teleporting during active dialogue, battles, movement, fades, linked activities or a Safari game. Every destination has been checked, but every story branch, capture, trade, gift and puzzle has **not** been completed end to end in live desktop play.

Locations and acquisition scope were checked against [pret/pokefirered](https://github.com/pret/pokefirered/tree/master/data/maps), then validated against the locally imported FRLG maps. The catalogue contains destination metadata only; original scripts and ROM data are not redistributed.

## Screenshot gallery

Native UI previews from development, using fixture state rather than live gameplay captures.

Historical preview (older build): [encounter-tour-categories](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/encounter-tour-categories.png).

Historical preview (older build): [encounter-tour-deoxys](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/encounter-tour-deoxys.png).

Historical preview (older build): [encounter-tour-events](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/encounter-tour-events.png).

Historical preview (older build): [encounter-tour-home](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/encounter-tour-home.png).

Historical preview (older build): [encounter-tour-notes](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/encounter-tour-notes.png).

## 0.1.1 compatibility update

Uses the shared `src.core.CollPermissions` predicates instead of importing the Gen 2 wrapper. This preserves landing checks and fixes rejection by the current host’s cross-generation mod guard. Required alongside the Gen3DualScreen collection build.

## 0.1.2 dual-screen integration

Adds explicit detached editor ownership for Gen3DualScreen 0.2.0 and reports active tours to its encounter browser. Live browsing forwards field updates; running tours keep their own controls. Includes the 0.1.1 shared collision-helper fix.


## Native Pokémon legality corrections — 0.1.3

This release includes the shared FRLG generation/export corrections. It sets valid ability slots for newly generated/caught Pokémon, creates native gift eggs with the correct egg metadata, preserves fixed NPC-trade identity and contest values, and generates new roamers with retail FRLG PID/IV correlations. The roaming beast's stored personality and IVs now reach the battle without being regenerated. Native unhatched eggs receive the required OT-name padding during in-game export.

The same helper is bundled independently with Dual Screen, Shiny Hunter, Encounter Reset, Encounter Tour, Day Care Viewer and Pokémon Services. No additional mod is required. Co-loading these packages applies the corrections once; disabling every participating mod or unloading the game stops the wrappers. Existing Pokémon are not rerolled or bulk-repaired.

**For a cartridge save, use MODS → this mod → SAVE + EXPORT while in the field.** This first saves the active game and then exports with the egg-name correction loaded. The log gives the output path under `exports/<edition>/`. A fresh launcher export can still use the host's unpatched egg-name encoder; copy the in-game export directly. Restart after installing updates.

See the collection's `docs/LEGALITY-FIXES.md` for the regression results and limits. This corrects the identified defects; a passing sample matrix does not certify every possible modified ROM, species combination or future host release.

## Current starter menus

Native UI previews with synthetic state; these do not represent a completed gift or a fresh legality check.

![Emerald starter menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/encounter-tour-emerald-starters-detail.png)

![FRLG starter menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/encounter-tour-firered-starters-detail.png)
