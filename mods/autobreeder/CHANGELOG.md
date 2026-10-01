# 1.0.3

- Keep either current improved parent, with confirmation, from the R-button parent menu or result actions, even after claiming the result.
- Pause active searches while choosing parents. Preserve original parents, refuse duplicate claims, allow newly promoted parents to be kept, and retain unclaimed parents when storage is full.
- Preserve generated parent PID, IVs, moves, origin and export marker; PC delivery uses native healing. Add engine/UI regression tests and PKHeX export samples for improved parents.

# 1.0.2

- Fix the missed desktop export lifecycle: returning to the launcher restarts Lua and removes the mod's exporter correction. Add a confirmed in-game Save + export action so the corrected GBA file is written before restart.
- Warn against overwriting the corrected file with a fresh launcher export. Retire the incorrect 1.0.1 export instructions.
- Reproduce the supplied Box 5, slot 1 Charmander egg's exact PKHeX terminator error. A separate repaired save changes only two OT padding bytes and passes PKHeX without changing PID, IVs or other Pokémon.
- Add export lifecycle, save failure, write failure and confirmation regressions; verify negative-control and corrected full saves in both editions.

# 1.0.1

- Fix the single-ability export defect affecting odd-PID Charmander and other single-ability species. Persist the correct ability slot without changing the generated personality or IVs.
- Correct exported OT-name padding for marked Auto Breeder eggs and hatchlings.
- Add a confirmed party/PC repair action for existing bred results with the old ability-slot defect.
- Add a broad PKHeX matrix: 11,268 Pokémon pass, including both PID parities for six-perfect Charmander and direct reading of two full GBA saves.
- Expand automated engine/UI checks to 372 passing assertions.

# 1.0.0

Initial release. Superseded because its ability-slot export fallback could produce illegal single-ability Pokémon. Update and repair affected results with 1.0.1.
