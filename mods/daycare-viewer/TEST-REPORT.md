# Day Care Viewer verification

Tested 27 September 2026 against the locally available upstream checkout `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf` and imported FireRed / LeafGreen data. Tests use synthetic sessions and do not access player saves.

- 82/82 native integration and UI assertions plus 28/28 native travel assertions per edition, 220 total.
- Native module loading, start-menu insertion before SAVE, duplicate-entry prevention, six-row navigation, nested START close, session-change close and selected frame setting.
- Deep equality of empty and populated session state before/after inspection and browsing; RNG unchanged.
- Save-backed and session-alias storage; Route 5 and Four Island; native cost, level and automatic move-learning agreement; level 100.
- Countdown boundaries at 0, 1, 254, 255, 256, 510, 511 and 65535 steps, using the second parent's count rather than the party hatch counter.
- Pending egg, split Nidoran offspring, Sea Incense, Ditto/Ditto, Undiscovered and same-gender incompatibility, and party hatch-cycle estimates.
- Preview explicitly rejects any call to Experience.apply, which would emit gameplay level-up events to other mods.
- Thirteen native UI renders visually inspected for layout and clipping.
- Native deposit/withdraw handlers, original Pokémon identity, daycare-use stat, fees, learned moves, insufficient funds, full daycare/party, pending-egg protection, last usable Pokémon, stale selections/quotes, changed session and busy-state rejection.
- UI confirmations default to Cancel; explicit confirmation uses the native action and charges the displayed fee.
- Native warps to both daycare interiors and original attendant dialogue from both landing points in both editions. Missing/occupied landings and locked/moving/linked states reject travel; UI teleport closes both DAY CARE and START.
- Strict modkit validate and gen3check, plus lint: pass.

Full live playthrough, physical controller/Android device testing and arbitrary third-party breeding changes have not been tested. Unit rendering uses the host's headless graphics stub; screenshots separately use real imported font/frame drawing traces.

## Reproduce

From a matching Gen1Recomp source checkout, with LuaJIT installed:

```sh
export LUA_PATH='./?.lua;./?/init.lua;;'
export DAYCARE_ROOT=/path/to/gen1recomp-mods/mods/daycare-viewer
export POKEPORT_VERSION=firered
export POKEPORT_GBA_CACHE=/path/to/firered/data/generated/gba
luajit /path/to/gen1recomp-mods/tools/daycare-viewer/integration.lua
luajit /path/to/gen1recomp-mods/tools/daycare-viewer/travel_test.lua
```

Repeat with `leafgreen` and its imported cache. No ROM-derived assets are included in the mod. Test and screenshot helpers are in `tools/daycare-viewer` and deliberately excluded from the installable archive.

To render demo screens, create a scratch directory and run:

```sh
luajit /path/to/gen1recomp-mods/tools/daycare-viewer/capture.lua "$DAYCARE_ROOT" "$POKEPORT_VERSION" "$POKEPORT_GBA_CACHE" /path/to/scratch
python3 /path/to/gen1recomp-mods/tools/render-manager-traces.py /path/to/scratch
```

Do not distribute the intermediate traces: they reference your local imported assets.
