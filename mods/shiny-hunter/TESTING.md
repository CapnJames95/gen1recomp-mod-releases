# Tests

Run from the root of a checkout of gen1recomp containing this mod at `mods/examples/shiny_hunter`. Use LuaJIT. Engine tests require the user's existing imported ROM cache; no cache is distributed with the mod.

```sh
luajit mods/examples/shiny_hunter/tests/controller_test.lua
POKEPORT_GBA_CACHE="/path/to/firered/data/generated/gba" luajit mods/examples/shiny_hunter/tests/engine_test.lua
SHINY_HUNTER_GAME=leafgreen POKEPORT_GBA_CACHE="/path/to/leafgreen/data/generated/gba" luajit mods/examples/shiny_hunter/tests/engine_test.lua
MODKIT_LUAJIT=luajit python3 tools/modkit.py validate mods/examples/shiny_hunter
MODKIT_LUAJIT=luajit python3 tools/modkit.py lint mods/examples/shiny_hunter
```

The engine suite creates synthetic test sessions with ROM-derived game logic. It does not load or overwrite the user's saves. LÖVE filesystem writes go to the in-memory test shim; the mod-storage facade is also in memory.

Assertions exercise battle construction and rollback, advancing RNG, party/money restoration, gift and egg factories, naturally generated shiny preservation, static encounter scripts, actual input queue injection, START pause, frozen menus, speed restoration, normal capture with ball consumption, route recording/replay, cave walking, registered-rod fishing, surfing recovery and Safari recovery. The suite also loads the mod through the production Loader, Sandbox and Storage with real Input, PlatformHooks and FixedStep execution. The controller suite covers foreign gifts, existing roamers, missing trainer IDs, full stop, limits, capture outcomes, and protection outside target filters.

Remaining manual QA: all individual story gifts/starters/fossils/prizes, Rock Smash rocks, Safari capture/flee outcomes, full roamer-release story path, touch/gamepad layouts and compatibility with other active mods. The source README separates tested coverage from implemented generic adapters.

Verification also runs this suite against an isolated extracted copy of the installed gen1recomp 0.3.21 update payload, with the test helpers supplied from the development checkout. Both FireRed and LeafGreen pass. No live saves, installed game files or installed mods are changed.

Second verification adds 72 controller assertions in total, duplicate-acquisition versus PC-move checks, and START-before-reset preservation through production hooks at 8× hunt speed.

High-speed regression/stress invocation (set the cache and LuaJIT as above):

```sh
SHINY_HUNTER_SPEED=256 SHINY_HUNTER_ATTEMPTS=100 SHINY_HUNTER_BUDGET_CLOCK=1 POKEPORT_GBA_CACHE="/path/to/firered/data/generated/gba" luajit mods/examples/shiny_hunter/tests/engine_test.lua
```

Repeat for LeafGreen with `SHINY_HUNTER_GAME=leafgreen`. Speed defaults to 256 for the production-hook test; attempt count defaults to 2. Stress runs used 100 attempts at 8, 64 and 256 in each game, then 100 at 256 with the CPU clock enabled. The naturally generated shiny fixture is introduced as a new battle afterward to assert exactly one fixed tick to detection and zero further world ticks behind the found menu. Frame counts are headless test measurements, not live desktop throughput guarantees.
