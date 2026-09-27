# Summary IVs 0.1.0 — FireRed / LeafGreen

Adds **IV 0–31** beside HP, Attack, Defense, Sp. Atk, Sp. Def and Speed on the native **Pokémon Skills** summary page, in the orange gap between the labels and stat totals. Uses the game's small font and normal text colours, matching native FRLG/LegalMon styling. The original right-hand numbers are calculated stats, not EVs; they remain unchanged.

![IVs beside the native stat labels](../../docs/screenshots/summary-ivs/firered.png)

## Install and configuration

Import `summary-ivs-0.1.0.zip` using **MODS → Import mod .zip**, enable **Summary IVs** for your edition and restart the session. Alternatively, copy this folder into the game's mod directory so `summary-ivs/manifest.json` is directly inside it. Do not install two copies.

Open a Pokémon's Summary and switch to **Pokémon Skills**. No extra button or submenu is needed. **SHOW IVS** in this mod's settings turns the column on/off; it defaults to on. Works for party and PC summaries using the native renderer. Eggs and enemy summaries are excluded. Missing/invalid IV data displays `--`, never a guessed zero. The column hides during page animations and refreshes when changing Pokémon.

This is read-only: no stat recalculation, EV/IV editing, save changes, RNG draws or altered controls. Expanded Summary Info can remain enabled for its separate nature/EV details menu; neither mod requires the other.

## Dual Screen

Use **FRLG Dual Screen 0.3.13 or newer**. With this mod enabled, its Skills page uses the native orange summary on the companion screen rather than Dual Screen's custom stat panel. Physical controls navigate it; the native fallback does not add touch hit targets. Disabling SHOW IVS restores the companion adapter. Older Dual Screen versions replace this page and do not show the inline column; update Dual Screen or disable it.

## Compatibility and validation

API 2, `engine_internals`, FireRed and LeafGreen beta. Tested against upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`; other engine versions or third-party summary replacements may need adaptation. No ROMs, extracted textures, fonts or player saves are included in the mod.

46 native-data checks pass per edition (92 total), including all six mappings, zero/31, invalid data, PC selection, toggle/reload/unload, session changes, animation guards and unchanged native text/stat positions. Native render traces were rendered and visually inspected for both editions. Collection tests exercise the Dual Screen fallback and toggle. Physical-device gameplay has not been tested for this addition.

Reproduce from the engine checkout:

```sh
LUA_PATH='./?.lua;./?/init.lua;;' luajit /path/to/collection/tools/summary-ivs/test.lua /path/to/collection firered /path/to/firered/data/generated/gba
```

Repeat with `leafgreen` and its imported cache. Tests use synthetic Pokémon, never your saves.
