# Distribution fidelity audit — 1.3.0

This release adds verified distribution results to the existing archive. It does not execute event ROMs or claim complete historical coverage.

## Added and corrected

- **Trade and Battle Day / JEREMY:** nine preserved English specimens: Ekans, Vulpix, Oddish, Psyduck, Growlithe, Machamp, Gengar, Staryu and Tauros. The official archive's original `.pk3` records are used, preserving OT, IDs, PID, IVs, moves, held items and even unused nickname bytes. Machoke and Haunter evolved when traded, so the received choices are Machamp and Gengar. Specimens are fixed; no speculative shiny reroll is offered. Renaming a received Pokémon still works normally.
- **Wishing Star Jirachi:** restores the second PKHeX distribution definition that had been merged with the first. The original restricted-table version and the alternate recipient-gender version have separate choices. Both retain ネガイボシ and ID 30719; only the latter's OT gender follows the recipient. Both carry a documented Salac Berry. The alternate choice does not reset an earlier claim.
- **Gotta Catch 'Em All / Japanese Pokémon Centers:** city OT selection for all 58 existing choices. First–Fifth offer Tokyo, Yokohama, Nagoya, Osaka, Fukuoka and Sapporo. Sixth offers the first five only. City options share the existing Pokémon claim. These are generated valid regional variants, not newly recovered event specimens.
- **Mt. Battle Ho-Oh:** adds Japanese, French, German, Italian and Spanish language results alongside English, using the language-specific OT definitions in PKHeX's Colosseum gift generator. These remain non-shiny bonus rewards.
- **Eon Ticket:** all eight normal/shiny Ruby, Sapphire and Emerald replica templates now carry Soul Dew, matching the original Southern Island encounter script.
- **Mystic Ticket:** adds separate LeafGreen-origin caught replicas. Native journeys select the current game's origin. A previously received counterpart no longer blocks claiming the remaining Pokémon; successful ticket delivery suppresses the already-used encounter to enforce one claim. Failed/cancelled delivery changes no encounter flags. Original fought/ticket flags are never reset. Version 1.2 LeafGreen native reservations, which used FireRed catalogue claim keys, are recognized without rewriting receipts.

All 305 previous claim IDs remain present. The resulting archive has **87 campaign menus, 322 Pokémon choices and 670 selectable variants** (including city and language variants).

## Deliberately excluded

- **JEREMY Sandshrew, Slowpoke and Shellder:** the first two records have been disputed as fake, and Shellder lacks a confirmed preserved specimen in the vetted nine-specimen archive. Devolved Machoke/Haunter reconstructions are also excluded.
- **Pokémon Stamp Pichu/Absol:** unresolved original identity/data and no sufficiently verified preserved source for faithful addition. PKHeX acceptance alone would not establish their historical accuracy.
- **Altering Cave distributions:** no released campaign has been established; unused game support is not presented as a released distribution.
- **Eon Ticket and Old Sea Map travel in FRLG:** their islands/scripts belong to RSE. Caught replicas retain those source games. Old Sea Map Mew remains Japanese Emerald only.
- **GBA e-Reader berries, decorations and Trainer Hill/Trainer Tower cards:** these require their original game-specific systems. They are not Pokémon distribution gifts, and are not converted into invented FRLG events.

## Sources and reproducibility

- [Official Project Pokémon JEREMY preservation archive](https://projectpokemon.org/home/files/file/3779-trade-and-battle-day-jeremy/) and [preservation discussion](https://projectpokemon.org/home/forums/topic/59333-trade-and-battle-day-jeremy-pokemon/). `tools/fidelity-sources.json` records the downloaded archive SHA-256 and hashes of all nine included specimens. The augmentation tool rejects any different source file.
- [PKHeX event definitions, pinned revision](https://github.com/kwsch/PKHeX/blob/17157eb18013dc29a44f7bb7810117390431087b/PKHeX.Core/Legality/Encounters/Data/Gen3/EncountersWC3.cs): Wishing Star's two methods.
- [PKHeX Japanese distribution definitions](https://github.com/kwsch/PKHeX/blob/17157eb18013dc29a44f7bb7810117390431087b/PKHeX.Core/Legality/Encounters/Templates/Gen3/Gifts/Distribution3JPN.cs): permitted city OTs.
- [PKHeX RSE/Colosseum encounter definitions](https://github.com/kwsch/PKHeX/blob/17157eb18013dc29a44f7bb7810117390431087b/PKHeX.Core/Legality/Encounters/Data/Gen3/Encounters3RSE.cs): Mt. Battle Ho-Oh reward. Language OTs come from its gift generator.
- [Emerald Southern Island encounter script](https://github.com/pret/pokeemerald/blob/master/data/maps/SouthernIsland_Interior/scripts.inc): Soul Dew.
- [FireRed/LeafGreen Navel Rock summit script](https://github.com/pret/pokefirered/blob/master/data/maps/NavelRock_Summit/scripts.inc): original Ho-Oh encounter visibility/progress behavior.
- [Stamp Pichu research](https://projectpokemon.org/home/forums/topic/66304-stamp-pichu/): why guessed Stamp identities are excluded.

Generate/enrich the base catalogue using `tools/Program.cs`, then run `--fidelity <enriched-catalog.json> <extracted-official-jeremy-directory> <augmented-catalog.json>`. Compile the augmented catalogue with `tools/catalog.py <augmented-catalog.json> <mod-directory> <English-move-name-list>`. The helper uses the pinned PKHeX assembly; generated variants are validated before inclusion. Runtime catalogue bytes are shipped, so normal play requires no generator, archive download or PKHeX installation.

## Verification

Against gen1recomp `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf` and PKHeX `17157eb18013dc29a44f7bb7810117390431087b`:

- 1,340 byte-exact fixture exports across FireRed and LeafGreen.
- 5,216 personalized exports across both games and 20 trainer profiles.
- 8,300 exports covering actual eggs, engine hatching and native island captures.
- 40 additional exports covering fixed JEREMY records and both recipient genders for alternate Wishing Star Jirachi.
- **14,896/14,896 PKHeX-valid exports.** Restricted requests are reported unavailable rather than altering trainer IDs.
- Regression checks cover partial Mystic claims in either direction, failed delivery, stale selections, old LeafGreen native receipts, Soul Dew, distinct city OT previews, fixed specimen export/renaming, all 670 menu paths and save serialization.

These are automated headless engine tests, not a claim of manual live gameplay or proof of original attendance.

## Repeat-generation audit (1.4.5)

The catalogue's stored records remain reference templates. Runtime generation now covers every non-preserved choice (313 of 322), with only the nine JEREMY archive specimens retaining fixed PID/IVs. Event-OT generation follows the documented correlations and gender rules in [PKHeX's Gen III event implementation](https://github.com/kwsch/PKHeX/tree/542111fc8584ff29c9d1455553b8acd0e1f8a59a/PKHeX.Core/Legality), including CommonEvent3, EncounterGift3, the NY/JPN/Colosseum gifts, ChannelJirachi, MYSTRY Mew's released seed set and Wishmkr's held-item rule. Credit: kwsch and PKHeX contributors (GPL-3.0; see LICENSE).

`tools/event-distributor/build-policies.py <EncountersWC3.cs> <MystryMew.cs>` regenerates claim-specific policies and the released MYSTRY seed set from that revision. The two regression drivers beside it exercise repeated menu redemption and export three consecutive results per available variant in each game. Restricted personalised variants without a different legal result remain unavailable. The independent PKHeX checker accepted all 5,943 exported records. Original templates and claim IDs are unchanged.
