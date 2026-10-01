# Pokémon legality fixes — 27 September 2026
> **Historical report.** Version numbers and test results below describe their recorded development snapshots. Current versions and installation status are in [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md); screenshot freshness is recorded in [the image audit](SCREENSHOTS.md).


**All 438 sampled Pokémon now pass PKHeX, including all 18 previously rejected records.** FireRed and LeafGreen were tested separately. Complete cartridge-save exports also pass: **46 saves, 50 Pokémon, zero legality or checksum failures**.

## Updated downloads

| Mod | Version | Download |
| --- | --- | --- |
| Gen3DualScreen | 0.3.13 | [ZIP](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-dual-screen-0.4.14.zip) |
| Shiny Hunter | 0.1.5 | [ZIP](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/shiny-hunter-0.2.1.zip) |
| Encounter Reset | 0.1.1 | [ZIP](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/encounter-reset-0.4.0.zip) |
| Encounter Tour | 0.1.3 | [ZIP](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/encounter-tour-0.3.0.zip) |
| Day Care Viewer | 0.2.1 | [QoL Suite download](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-qol-suite-0.3.9.zip) |
| Pokémon Services | 0.1.1 | [QoL Suite download](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-qol-suite-0.3.9.zip) |

These packages carry the same shared engine compatibility corrections, so each works independently. Loading several installs one shared set of wrappers; disabling all participating mods restores native behaviour. Encounter Tour also carries the fixes because its travel routes reach the affected native generation paths.

## Corrections

- Native gifts and captures use the correct ability slot. Explicit imported and event slots remain authoritative.
- Gift eggs receive the proper met level, egg location and hatch-cycle data. Native egg exports retain the required original-trainer string terminator. Breeding recomputes the ability slot after replacing the initial personality value.
- Newly generated roamers use the retail personality/IV correlation, including FireRed/LeafGreen's restricted roamer IVs. The battle bridge preserves the stored personality and IVs instead of generating replacements.
- NPC trades retain their fixed trainer identity, ability slot and contest data.

Existing Pokémon are not rerolled or bulk repaired. Previously generated invalid roamers remain unchanged; the generation correction applies to new eligible resets. No player save or installed game was modified during this work.

## Installation and export

Replace the affected installed mods with these ZIPs and restart the game. To export with the egg encoding correction active, return to the field and use **START → MODS → one of the updated mods → SAVE + EXPORT**. The action saves first, exports only after a successful save, and reports the export path in the log.

A fresh desktop launcher's export runs without these in-game compatibility wrappers. Use the in-game action for corrected cartridge exports.

## Verification

- The original generation matrix was regenerated: **438/438 legal**, up from 420/438. LegalMon, Event Distributions and Auto Breeder continue to pass unchanged.
- Complete `.sav` files were parsed independently; all save checksums and all 50 nonempty party/box Pokémon passed.
- Actual SDK loader tests pass **135/135 checks per edition**, covering each package alone, all six together, disable/reload, imported data preservation, roamer RNG, save failure guards and the in-game export action.
- All 16 targeted regression jobs pass, including the full 37-mod collection suite, services, daycare and companion integrations on both editions.
- Strict manifest validation, lint and Gen 3 compatibility checks pass for all six packages (18 checks).

This is an automated pass against engine commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf` and PKHeX.Core 26.8.26.0. It does not establish compatibility with every host release or replace physical-device playtesting.

[Original failure details](LEGALITY-PASS.md) · Test tools · Record results · Save results · Regression results

The six new ZIPs pass integrity and complete source-parity checks. The broader collection packaging audit currently stops on an unrelated, already modified Ball Shortcut source/ZIP mismatch (`downloads/frlg_qol_ball_shortcut-0.2.1.zip`, `main.lua`). That package was not rebuilt as part of these legality fixes.

The later battle-tools update packages Ball Shortcut 0.2.2 and Dual Screen 0.3.6; it resolves the Ball Shortcut source/ZIP mismatch noted above.

A subsequent [different-species follow-up](LEGALITY-ALTERNATES.md) passed 96/96 additional Pokémon and all 96 complete-save exports through the previously failing paths.
