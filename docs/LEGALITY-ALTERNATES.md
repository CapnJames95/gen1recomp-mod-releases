# Additional Pokémon legality samples — 27 September 2026

**96/96 additional Pokémon pass PKHeX, with zero failures. All 96 complete-save exports also pass save checksums and Pokémon legality.** These exercise the same generation paths responsible for the original 18 failed records, using other species and independent RNG seeds on both FireRed and LeafGreen.

| Path | Records | Species sampled |
| --- | ---: | --- |
| Walking encounters | 10 | ELECTRODE, MACHOKE, MAGNETON, PARASECT, PRIMEAPE |
| Fishing encounters | 8 | GYARADOS, SHELLDER, STARYU |
| Safari encounters | 8 | EXEGGCUTE, NIDORAN♀, NIDORAN♂, RHYHORN, VENONAT |
| Static resets | 4 | ARTICUNO, MOLTRES |
| Roamer resets | 6 | ENTEI, RAIKOU, SUICUNE |
| Starters | 12 | CHARMANDER, SQUIRTLE |
| NPC trades | 16 | CH'DING, ESPHERE, MARC, MR. NIDO, MS. NIDO, NINA, NINO, SEELOR, TANGENY, ZYNX |
| Native daycare eggs and hatchlings | 20 | EEVEE, MAGIKARP, MAGNEMITE, PICHU, SQUIRTLE |
| Native gift eggs and hatchlings | 12 | TOGEPI |

Fishing used the Super Rod through Shiny Hunter's actual fishing automation. Safari used its actual walking/recovery loop. Walking samples used Dual Screen's route encounter action. Static samples reset Articuno/Moltres and interacted with the native encounter scripts; all three starter-dependent roamers were reset, encountered through the battle bridge, captured and exported. Starters, NPC trades and daycare samples used native factories. No Pokémon personality, IV or legality fields were edited after generation to make the samples pass.

FireRed/LeafGreen has one native gift-egg species, Togepi. That path was checked with three new RNG seeds per edition, both before and after hatching. Different egg species were checked through native daycare: Squirtle, Pichu, Eevee, Magikarp and Magnemite. NPC trade nicknames in the table are the cartridge-defined names.

Initial test-fixture attempts needed cleanup between roamer battles and restoration of temporary map-section fields before static captures. The final run uses corrected fixture lifecycle handling; no mod source or release ZIP changes were needed.

Engine: `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. Validator: PKHeX.Core 26.8.26.0. This is representative automated coverage, not an exhaustive test of every possible Pokémon or RNG result. Player saves were not modified.

[Reproduction script](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest) · [Generation runs](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest) · [PKHeX records](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest) · [Complete saves](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest) · [Sample hashes](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest)
