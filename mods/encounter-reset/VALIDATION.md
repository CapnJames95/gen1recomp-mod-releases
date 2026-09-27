# Validation — 0.1.0

Test host: gen1recomp `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`, local `/tmp/frlg-dual-upstream`, LuaJIT; separate imported FireRed and LeafGreen caches. No player saves are loaded or modified.

Passed for both editions:

- All 12 static entries: seed used/hidden/fled flags, reset selected entry, verify all other encounter flags and a badge remain set, preserve party/Pokédex references and money, enter original map, verify reset flags survive native transition scripts.
- Deoxys starts with a hidden Pokémon, visible puzzle and zero puzzle counters; Ho-Oh's temporary approach trigger is enabled.
- Current encounter map, locked field, movement and unknown entry rejection.
- Each of three starter choices: reject active/other beasts, regenerate the original inactive beast using the engine, retain species.
- Flag serialization and restoration retains badge state.
- START menu hook deduplication, default cancel, explicit confirm, field pause while open.
- Native interaction with the restored Zapdos reaches a battle with species 145.
- Strict modkit validation and Gen III compatibility check. Static analyzer reports indirect module references it cannot resolve; engine tests cover these paths.

Native home, Deoxys detail and confirmation screens rendered from real draw calls and imported font/sprite data. Home/detail inspected visually.

Not verified: complete catch-and-save round trips for every encounter; full Deoxys puzzle and Hypno rescue replay; physical controller/Android play; simultaneous automation mods. The reset preserves original scripts, including Hypno's quest replay and normal access requirements.

Reproduce from an upstream engine checkout, setting paths for your machine:

```sh
RESET_MOD=/absolute/path/to/mods/encounter-reset/ \
RESET_GAME=firered \
POKEPORT_GBA_CACHE=/absolute/path/to/firered/data/generated/gba \
/path/to/luajit /absolute/path/to/mods/encounter-reset/tests/engine_test.lua
```

Repeat with `RESET_GAME=leafgreen` and its cache. The test uses sibling Encounter Tour's adapter to enter maps; it is not a runtime dependency.

## 0.2.0 — gifts, fossils and NPC trades

Both FireRed and LeafGreen pass the expanded engine suite (30 stationary entries plus three roamer choices) and `tests/rewards_test.lua`. The rewards suite follows original map interactions to receive both Dojo prizes, all three fossils, Eevee, Lapras, Magikarp and the Togepi egg. It checks the fossil item is consumed, the native lab-entrance transition finishes revival, Magikarp costs 500, Togepi is an egg, and the other Dojo ball/shared claim remain unchanged. Headless audio completion is stubbed; generation and reward scripts remain native. The shared native legality helper is loaded.

Pending reset metadata survives a JSON round trip. Duplicate requests, competing fossil resets, an unfinished original revival and full-bag failure are rejected. Both version-dependent trade species mappings are checked. NPC trade availability flags and isolation pass for all nine traders; full trade animations are not replayed by this suite.

Run `tests/rewards_test.lua` with the same working directory/environment as the engine suite. Keep the mod enabled for pending Dojo/fossil collection. Manual Android/Thor play remains unverified.
