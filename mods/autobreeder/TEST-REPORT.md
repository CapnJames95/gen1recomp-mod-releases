# Auto Breeder 1.0.3 — legality regression report

## Improved parent retention

Added confirmed individual parent claims, available during paused/limited searches and after claiming the final result. Tests cover original-parent refusal, inactive/wrong sessions, repeat claims, independent copies, unchanged search/result state, full storage and PC retry with native healing, and keeping a newly promoted parent. UI tests cover cancellation, successful delivery, duplicate prevention and access after result claim.

Fresh export validation: **PKHeX.Core 26.8.26.0: 26/26 valid, zero failures, four complete saves read**, including four actual generated improved-parent samples (both slots, both editions). The earlier broad matrix below is retained as prior validation; generation rules are unchanged in this release.

## Export lifecycle regression and supplied save

The 1.0.1 tests kept the exporter patch installed. They missed that returning to the desktop launcher restarts Lua, removing the patch before the user exports. Version 1.0.2 adds an explicitly confirmed in-game save/export action. Launcher-only exports remain affected by the engine defect; use the in-game output directly.

The supplied LeafGreen save reproduces **Invalid: Final terminator missing** on the six-perfect Charmander egg in Box 5, slot 1. Its ability is already correct. OT bytes were `BBC8BED3FF0000`; changing only the final two bytes to `FF` produces **Legal!** in PKHeX.Core 26.8.26.0. The repaired copy differs at exactly two file offsets, 91805 and 91806 (zero-based). All save checksums pass. PID, all IVs and every other Pokémon byte are unchanged. The original file was not modified.

New lifecycle tests run the real save schema, serialization and GBA export code with in-memory persistence/filesystem and a save-method façade. Removing the codec wrappers reproduces fresh-launcher output exactly. Both negative-control saves reproduce the egg terminator error (4/6 Pokémon valid; 2 expected failures). Both in-game corrected saves pass (6/6 valid; zero failures). This is automated lifecycle simulation, not an interactive desktop restart test.

## Defect and correction

Version 1.0.0 did not populate `abilityNum`. Gen1Recomp's GBA exporter then defaulted it to `personality % 2`. This is wrong for single-ability species: an odd-PID Charmander must still use ability slot 0. PKHeX reports **Ability does not match ability number** for that error. The old test suite covered ability 2 on a dual-ability species and sampled other species; it did not cover odd-PID Charmander and was insufficient.

Version 1.0.1 explicitly records slot 0 when the ROM has no second ability, otherwise PID parity. It preserves the generated PID and IVs. The repair tool applies the same metadata correction to a selected existing bred Pokémon, after confirmation.

The beta exporter's OT-name padding also failed PKHeX for unhatched eggs. `export.lua` corrects that header field only for Pokémon marked as generated/repaired by Auto Breeder. The Pokémon's encrypted data, PID, IVs and checksum are unaffected by the name-padding correction. The marker survives native saves. Export through the mod's in-game menu, not after returning to the launcher.

## PKHeX results

**PKHeX.Core 26.8.26.0: 11,268 / 11,268 valid; 0 failures; 2 complete `.sav` files read directly.**

| Coverage | Details |
|---|---|
| Editions | FireRed and LeafGreen |
| Species | All 351 compatible parent species in each imported edition; their native offspring are generated |
| General matrix | 8 samples per compatible parent species, each exported as egg and hatchling |
| Special breeding | Male/female parents with Ditto, split offspring species, incense/no-incense outcomes, native inherited moves |
| Charmander regression | Actual generated six-perfect eggs with even and odd PIDs, each exported unhatched and hatched |
| Trainer/shiny cases | One-character and seven-character OT names, both trainer genders, boundary trainer/secret IDs, actual shiny searches |
| Persistence | Native serialization before sample export; party/PC results in full GBA save exports |
| Repair | Odd-PID six-perfect Charmander with an intentionally wrong ability bit, repaired without changing PID or IVs |

The broad matrix produces 5,626 encrypted `.pk3` files per edition (11,252 total). Additional integration exports and the six occupied Pokémon in the two full save files bring the checked total to 11,268. Full saves are parsed directly by PKHeX's save reader; the check is not limited to isolated reconstructed Pokémon files.

The generated six-perfect cases use perfect parent test fixtures. The code never assigns target IVs to generated offspring. Ordinary-parent improvement also remains covered below.

## Engine and UI regression results

| Suite | Result |
|---|---:|
| FireRed integration | 175 / 175 passed |
| LeafGreen integration | 175 / 175 passed |
| Menus, parent claims, repair, export confirmation, hooks and production mod loader | 60 / 60 passed |
| FireRed save/export lifecycle | 18 / 18 passed |
| LeafGreen save/export lifecycle | 18 / 18 passed |
| **Total** | **446 / 446 passed** |

These retain the earlier checks for generation parity with the engine, inherited IVs/moves, complementary parent coverage, Ditto preservation, impossible targets, breeding groups, incense, baby offspring, PID-derived traits, shiny independence, attempts, pause/stop, RNG restoration after errors, one-time claiming, PC fallback, full storage, session isolation and save round trips. Added regressions cover single-ability PID parity, existing-result repair, repair cancellation, exporter idempotence, untouched unrelated Pokémon, OT padding and complete save export.

Fixed-seed searches still find a six-perfect egg after 31,716 attempts from perfect test parents; ordinary random-IV parents produce a six-perfect match after 46,536 attempts and 12 upgrades. A shiny-only test finds a match after 3,619 attempts. These are test cases, not completion-time guarantees.

## Environment and scope

- Actual installed Gen1Recomp **0.3.21** release modules and both already-imported game editions.
- Upstream reference: `84e076b2d1e2dda36073ff55ec7c311a6b97519c`; its breeding module matches the installed payload.
- LuaJIT, the production mod loader, native save/export code, imported species/move data, and the separately built PKHeX checker.
- Regression test sessions and save files are synthetic. The separately supplied player save was inspected and repaired into a new copy; the original was not overwritten.
- Full interactive playthrough testing remains unverified. Native UI drawing operations were rendered with imported fonts, frames and sprites and visually inspected in the initial release; menu/repair interaction is covered by automated tests.
- This is broad validation against the stated PKHeX version, not a claim about arbitrary third-party ROM changes, externally edited Pokémon, or future checker changes. The repair action corrects the reported ability metadata defect; it is not an unrestricted legality editor.

## Reproduce

Use `tests/integration.lua`, `tests/ui.lua`, `tests/legality_matrix.lua` and `tests/LegalityCheck/` with the commands in `README.md`. The installable archive excludes tests, imported assets, PKHeX binaries and generated Pokémon. The source archive includes the test code.
