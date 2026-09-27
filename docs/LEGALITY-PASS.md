# Pokémon generation legality pass — 27 September 2026

**Historical baseline:** all 18 failures below are resolved in the [legality fixes and updated downloads](LEGALITY-FIXES.md). The new run passes 438/438 records.

**420 of 438 freshly generated encrypted Pokémon records passed PKHeX; 18 failed.** Every record passed its checksum check. FireRed and LeafGreen were tested separately. The failures are in native engine generation/export paths; the sampled direct-generator outputs all passed.

| Generator / path | Passed | Failed | Coverage |
| --- | ---: | ---: | --- |
| LegalMon | 124 | 0 | 62 acquisition/RNG/origin families per edition: starters, fossils, gifts, prizes, statics, roamers, ticket legendaries, fixed trades, breeding, H1/H2/H4 land/water/three rods/Rock Smash, Unown, restricted events and GameCube variants. |
| Event Distributions | 210 | 0 | Fixed distribution/RNG families, personal-OT RNG families and origins, shiny/nonshiny variants, unhatched/hatching events, plus actual Aurora/Mystic ticket battle/capture output. |
| Auto Breeder | 60 | 0 | Perfect eggs, improving parents, nature/gender/ability filters, shiny eggs/hatchlings, second ability, same species, Ditto, genderless, baby offspring, both incense branches, both Nidoran and Volbeat/Illumise outcomes, inherited Bite, and save-round-tripped party records. |
| Dual Screen | 10 | 2 | One each of WALK, SURF, Old Rod, Good Rod, Super Rod and Rock Smash per edition, through the native route encounter API and capture/export. |
| Encounter Reset | 0 | 4 | Reset native Zapdos interaction and newly regenerated Suicune roamer per edition. |
| Encounter Tour | 2 | 0 | Native Zapdos script after actual tour warp, then capture/export. |
| Shiny Hunter | 4 | 4 | Real unattended cave walking, fishing, Surf and Safari battle samples per edition. |
| Native gift / trade / daycare factories | 10 | 8 | Starter, fossil, gift, Game Corner prize, Togepi gift egg before/after hatching, NPC trade, and native daycare egg before/after hatching. These are shared engine paths reachable through hunting/travel/daycare tools; factory calls are tested directly, not every story interaction. |

## Failures

Each row below failed in **both FireRed and LeafGreen**. These are reproducible failures of the exported records, not merely internal mod warnings.

| Path / sample | PKHeX rejection |
| --- | --- |
| dual-walk — GOLBAT | Invalid: Ability does not match ability number. |
| encounter-reset-roamer — SUICUNE | Invalid: PID+ correlation does not match what was expected for the Encounter's type.; Invalid: Ability does not match ability number. |
| encounter-reset-static — ZAPDOS | Invalid: Ability does not match ability number. |
| native-daycare-egg — タマゴ | Invalid: Final terminator missing. |
| native-gift-egg — タマゴ | Invalid: Invalid Met Level, expected 0.; Invalid: PID+ correlation does not match what was expected for the Encounter's type.; Invalid: Invalid Egg hatch cycles.; Invalid: Final terminator missing. |
| native-npc-trade — MIMIEN | Invalid: Unable to match an encounter from origin game. |
| native-starter — BULBASAUR | Invalid: Ability does not match ability number. |
| shiny-hunter-fishing — MAGIKARP | Invalid: Ability does not match ability number. |
| shiny-hunter-safari — NIDORINO | Invalid: Ability does not match ability number. |

## What the failures mean

- **Ability slot:** the tested host exporter uses `personality % 2` when a Pokémon lacks an explicit `abilityNum` (`src/save_convert/Gen3Save.lua:1280`). This can emit slot 1 for a species that only has slot 0. The failing Zapdos has an odd PID; the passing tour Zapdos has an even PID. A passing single sample on this shared path therefore does not guarantee that later encounters will pass. LegalMon and Auto Breeder explicitly supply appropriate ability slots.
- **Reset roamers:** Encounter Reset calls the host’s `Roamer.init`. The host generates six full-range IVs rather than retaining the retail FRLG roamer IV restriction, and the tested captured Suicune fails PID/IV encounter correlation. See `src/core/game3/roamer.lua:131` and `mods/encounter-reset/adapter.lua:52`.
- **Native gift eggs:** `Party.giveEgg` derives a normal level-5 gift and marks it as an egg. The sample fails egg met-level, PID correlation, hatch-cycle and terminator checks. Its hatched sample passed.
- **Native daycare eggs:** the unhatched Charmander fails the final name-terminator check; its hatched counterpart passes. Auto Breeder’s tagged export correction does not apply to ordinary native eggs.
- **NPC trade:** native Mr. Mime could not match an origin encounter. The exact record and diagnostic are retained; this pass has not isolated the specific field responsible.

These are test findings, not fixes. Mod implementation, host implementation, installed files and player saves were not changed. Teleporting, monitoring encounters or inspecting daycare does not itself ensure cartridge legality.

## Scope and evidence

“Pass” means that this specific encrypted Gen III record is accepted by **PKHeX.Core 26.8.26.0**, including checksum validation. It does not establish historical event authenticity or certify every seed, trait combination, save state or later checker version. This is a representative generation-family pass, with extra samples for differing RNG, origin, shiny and egg branches. It is not a blanket legality guarantee.

Tests used local engine commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`, LuaJIT, existing imported FireRed/LeafGreen data and isolated synthetic sessions. Native encounter records were stored with the host capture routine and exported through normal save conversion; no PID/IV/ability repair was applied to make failed samples pass. Direct generators used their own normal export support. Native trade/gift and daycare helpers were exercised directly using synthetic, valid acquisition contexts.

- [Machine-readable summary](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest)
- [Every sample, generation family, SHA-256 and verdict](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest)
- [Raw final PKHeX output](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest)
- [LegalMon generation-family manifest](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest)
- [Event generation-family manifest](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest)
- [Test helpers and checker source](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest)

The encrypted `.pk3` samples and synthetic `.sav` files remain outside the release repository at `/tmp/mod-legality-pass/samples`. No ROM assets or PKHeX binary were added to the repository.
