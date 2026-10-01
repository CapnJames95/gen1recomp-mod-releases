# Pokemon Services validation

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


Validated 27 September 2026 against Gen1Recomp commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`, using separately imported FireRed and LeafGreen data. No player saves were loaded or written.

- **194/194 per edition:** real mod loader, original script discovery and service entry; 14 town/island inventories and 5 department-store counters; native shop buying, insufficient funds and cancellation; exact native healing agreement; Day Care deposit/paid withdrawal/stale selection; original Pokemon PC and item PC screens; field/movement/linked-activity/modal/session guards; START and Mods launch actions and native menu handoffs.
- The same suite runs the original service scripts and the free reminder sequence of native specials to completion with automated dialogue/selection input: all four Two Island stock stages; vending drinks at $200/$300/$350 and insufficient funds; own/traded Name Rater outcomes; native HM deletion; free move relearning with zero mushrooms and with each mushroom type already owned (inventory unchanged); cancellation, Egg and no-eligible-moves checks. The game's real mutation adapters are retained; only presentation/input waits are automated.
- **7/7 per edition:** services and Dual Screen load together, Home tile discovery and launch, duplicate START entry hiding, native PC handoff, START entry restoration with companion disabled.
- Modkit **lint**, **validate**, **gen3check** pass. The compatibility scanner notes unresolved dynamic call sites; the runtime suites cover their use. Its verdict is “will load,” not a gameplay certification.
- Six screens rendered from actual drawing code and locally imported fonts; home and department-store layout visually inspected. Screenshots use fixture data.

## Reproduce

From the engine source checkout:

```sh
export LUA_PATH='./?.lua;./?/init.lua;;'
export SERVICES_ROOT=/path/to/gen1recomp-mods/mods/pokemon-services
export POKEPORT_VERSION=firered
export POKEPORT_GBA_CACHE=/path/to/firered/data/generated/gba
luajit /path/to/gen1recomp-mods/tools/pokemon-services/integration.lua
luajit /path/to/gen1recomp-mods/tools/pokemon-services/dual_test.lua
```

Repeat for `leafgreen` and its cache. The Dual Screen test requires the sibling `mods/frlg_dual_screen` package containing the Services tile. `script_cases.lua` is invoked by the integration suite.

```sh
MODKIT_LUAJIT=/path/to/luajit python3 /path/to/engine/tools/modkit.py --repo /path/to/engine lint "$SERVICES_ROOT"
MODKIT_LUAJIT=/path/to/luajit python3 /path/to/engine/tools/modkit.py --repo /path/to/engine validate "$SERVICES_ROOT"
MODKIT_LUAJIT=/path/to/luajit python3 /path/to/engine/tools/modkit.py --repo /path/to/engine gen3check "$SERVICES_ROOT"
```

Physical device/controller playtesting, extended interactive playthroughs and arbitrary combinations of third-party mods have not been completed. Tests use synthetic sessions and the imported game data; they do not certify engine behavior beyond the exercised paths.
