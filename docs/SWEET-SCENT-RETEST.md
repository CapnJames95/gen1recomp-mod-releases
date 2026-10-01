# Sweet Scent upstream fix — 0.3.42

The [0.3.42 release](https://github.com/bryanthaboi/gen1recomp/releases/tag/v0.3.42) closes [report #2601](https://github.com/bryanthaboi/gen1recomp/issues/2601). Fix commit: `fc7da4dd2a2ce68ad45daa1b5234027c31fb9ff9`; tested release commit: `8e83d0bea70beb9c9795213510707ecb2c5025d9`.

| Game | Native test location | Result |
| --- | --- | --- |
| FireRed | Route 1, grass (10, 6) | Battle starts |
| LeafGreen | Route 1, grass (10, 6) | Battle starts |
| Emerald | Route 101, grass (2, 2) | Battle starts |

Each test starts a fresh LuaJIT process, enables Safe Mode through the native loader, verifies zero loaded mods and uses a synthetic session with a level-20 Oddish that knows Sweet Scent (move 230). The native Party menu invokes the field action. Native presentation/effect steps complete, then normal game updates advance the battle transition. Encounter generation, field actions and the battle bridge are not patched. This repeats the earlier failing route on the fixed engine.

The fix replaces the missing `Encounters.tryBattle` call with native Sweet Scent generation and `BattleBridge.startWild`. `Encounters.tryBattle` remains absent; that is no longer a failure because the repaired path does not call it. The tested field implementation and FRLG/Emerald encounter-rule files match the Mac's downloaded 0.3.42 update payload byte-for-byte.

## Scope and reproduction

These are automated source-engine tests with imported local data, not manual Mac/Thor gameplay captures or a complete collection compatibility run on 0.3.42. They establish the ordinary land-encounter path in all three games, not exhaustive water, weather or Frontier behavior. No app, installed mod, player save or settings were modified.

Run the harness from an unmodified 0.3.42 engine checkout with LuaJIT, setting `POKEPORT_VERSION` to each of `firered`, `leafgreen`, `emerald` and `POKEPORT_GBA_CACHE` to that edition's imported `data/generated/gba` directory. Success ends with `PASS: native Party Sweet Scent starts an encounter with zero mods.`

Use engine 0.3.42 for the upstream fix. The original unmodded retest used a Pokémon that knew Sweet Scent. Suite 0.3.9 now adds the optional Field Kit extension below; no experimental engine workaround is needed. Existing 0.3.39 compatibility evidence elsewhere is retained with its original test scope.

## HM Field Kit 0.2.4 integration

QoL Suite 0.3.9 lets any non-egg party member supply Sweet Scent without teaching it. Six native-engine runs pass: Field Kit menu and Dual Screen tile in each of FireRed, LeafGreen and Emerald on 0.3.42. The test uses Magikarp knowing only Tackle, launches the real menu action and reaches an active battle. Moves and PP remain unchanged. Egg-only parties, disabled Field Kit, older engines, unrelated parties and non-encounter terrain are rejected; Cut still requires its HM and Dig still needs to be learned. The host encounter generator is unchanged.

Run the integration harness from the 0.3.42 source checkout, setting `FRLG_COLLECTION_PATH`, `POKEPORT_VERSION`, `POKEPORT_GBA_CACHE` and `SWEET_PATH=kit` or `tile`. These are synthetic ordinary land-encounter checks, not a complete gameplay or Frontier validation.
