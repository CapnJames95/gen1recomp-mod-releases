# Auto Breeder 1.1.2

Current companion preview (synthetic Emerald session; Dual Screen is optional):

![Current autobreeder menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-autobreeder.png)


**Frontier safeguard:** receiving generated Pokémon (including improved breeding parents) is blocked during an active Emerald Battle Frontier challenge. Pending results and event receipts are left unchanged.

**Upgrade from 1.0.0 or 1.0.1:** use **AUTO BREEDER → Export / repair / help → Save + export for PKHeX**. Returning to the desktop launcher restarts Lua and removes the export correction; the earlier instruction to load the mod and then export from the launcher was incorrect. Use the in-game exported file directly, and do not overwrite it with another launcher export. This action saves current game progress after confirmation.

Version 1.0.0 could also export an invalid ability slot for single-ability species such as Charmander. To repair an existing bred result, open **AUTO BREEDER → Export / repair / help → Repair old result's ability slot**, select it from your party or PC, confirm, then use **Save + export for PKHeX**. This preserves PID, IVs, moves and trainer identity; it does not fix unrelated legality problems in externally edited Pokémon.

A FireRed / LeafGreen / Emerald Gen1Recomp mod that searches generated eggs for your chosen IVs, shininess, nature, gender and ability. It uses the current engine's breeding routines and the same visual conventions as LegalMon 0.2.1: native FR/LG fonts, player-selected window frames, blue title bar, six-row menus and a sprite-based result screen.

## Install

1. Use Gen1Recomp **0.3.39** with an imported FireRed, LeafGreen or Emerald game.
2. Import **autobreeder-1.1.2.zip** through the launcher's mod manager, replacing the old Auto Breeder version, then enable **Auto Breeder** for the edition you play. Allow the declared `engine_internals` permission if the manager asks; the mod needs the game-specific breeding and native menu APIs.
3. Load your playthrough and open **START → AUTO BREEDER**.

If installing manually, place the `autobreeder` folder under the mod directory shown by the launcher. `manifest.json` must be directly inside that folder. The mod contains all its Lua source; no compilation, ROM distribution or LegalMon dependency is required. It can be enabled alongside LegalMon.

## Use

1. **Choose parents:** select two distinct hatched Pokémon from your party, Four Island Day Care (FR/LG) or Route 117 Day Care (Emerald). Alternatively select **Use both Day Care parents**. Route 5's single-parent training Day Care is not a breeding source.
2. **Offspring targets:** choose **all six IVs = 31**, or toggle individual IVs between 31 and Any. Set Shiny to Any/Yes/No, any of the 25 natures, gender, and a named ability available to the offspring. Every selected target must match the same generated egg.
3. **Search settings:** choose an attempt limit and enable or disable parent improvement. Default: six perfect IVs, other traits Any, 1,000,000 attempts, improvement enabled.
4. **Start breeding.** A pauses/resumes; B, L or START returns and pauses; R inspects the working parents. SELECT opens a stop/discard confirmation. At the limit, A adds another budget without resetting the count or parents.
5. At **MATCH FOUND**, press A and explicitly choose **Keep as egg** or **Keep hatched (Lv.5)**. Confirm to deliver one result to the party, or the first free PC slot if the party is full. Full storage retains the unclaimed result for retry. Save your game normally afterward.

Up/Down moves through rows; Left/Right skips five rows. IVs appear in **HP / Attack / Defense / Speed / Special Attack / Special Defense** order. Settings changes apply to a new search; they do not alter an existing search's targets.

**Keep improved parents:** press **R** on the search/limit screen, or choose **Keep / inspect improved parents** from the result actions (also available after keeping the result). Choose Parent 1 or Parent 2 and confirm. Each currently improved parent can be kept once, already hatched, in the party or the first free PC slot. Original parents, including an unchanged Ditto, cannot be duplicated. Opening this menu pauses an active search; resume explicitly afterward. If a slot improves again, the new parent can be kept separately. Full storage leaves it available for retry. Keep parents before discarding the search or quitting, then save/export normally through the mod. Older displaced parents are not retained.

Searches are bounded to a small amount of work per UI update. Closing the menu pauses and preserves progress in memory; reopening it resumes the same play session. **Quitting, reloading a save, changing playthrough, or reloading mods loses unclaimed results and search progress.** Kept Pokémon persist through the game's normal save system. The mod does not save the game automatically.

## What is authentic, and what is accelerated

The mod calls the installed engine's `setInitialEggData`, `inheritIVs`, `buildEggMoveset`, `applyStats` and `hatchMon` routines. Compatibility, egg groups, offspring species, split Nidoran/Illumise species, incense requirements, inherited moves and inherited IVs follow those APIs. Emerald can select an IV more than once; its search estimates account for that difference. Nature, gender, ability and shininess are evaluated from the generated personality and trainer identity. Selected targets filter results; they do not overwrite personality or IVs.

The stored ability slot is explicitly set to **0 for a species with no second ability**, and to PID parity when the ROM defines a second ability. Equal-but-present second abilities are retained. This matches cartridge behavior and prevents the beta exporter's fallback from assigning Charmander a nonexistent second slot.

**Export inside the game using Export / repair / help → Save + export for PKHeX.** This saves the active playthrough, then runs the native GBA exporter while the OT-name correction is installed. It writes `exports/<edition>/gen1recomp-<edition>-<slot>.sav` under the game's data directory; the full path is recorded in the mod log. The export corrects name padding only for marked Auto Breeder results. The marker survives normal saves, but the in-memory exporter correction does not survive returning to the desktop launcher. **Do not re-export from the launcher:** it can overwrite the corrected file with the original terminator defect. Copy the in-game export directly to the device running PKHeX.

Each attempt is a generated egg, not a step or a rejected Day Care compatibility roll. Walking, compatibility waiting time, collection and hatching time are accelerated. Egg personality creation uses the engine's pending-egg formula. Unhatched eggs record **Four Island (146)** in FR/LG and the **RSE egg location (0)** in Emerald, even if the tool is opened elsewhere. Immediate hatching records the current map through the engine.

Breeding uses **copies** of the selected parents. Working offspring can become virtual parents after engine hatching. Your original Pokémon, their held items, and any pending Day Care egg remain untouched; discarded attempts and displaced virtual parents are not added to your party or PC. Only explicitly kept matches and improved parents enter your game. Offspring that cannot themselves breed, such as baby Pokémon, are not promoted; evolving them is outside this tool's scope. Parent moves may change through ordinary inheritance across generations.

The search has a private copy of the engine RNG state. It advances the global RNG once when starting a new search to obtain a fresh starting point, then restores the live RNG after each search batch, including error paths. This reproduces the beta engine's egg-generation behavior, not an exact timing replay of the original cartridge.

## How parents improve

For each offspring, the mod evaluates replacement of either working parent:

- The resulting pair must remain compatible and preserve the possible offspring species, including incense and split-species behavior.
- Ditto is never replaced by its offspring.
- Combined coverage of all six perfect IVs cannot decrease, and estimated probability of satisfying the selected IV targets cannot decrease.
- A higher target probability wins. Ties prefer greater combined coverage, then more IVs perfect in both parents, then higher Day Care compatibility.

The odds calculation averages the 20 possible inherited-stat sets and both parents' chances for each selected stat. Untargeted stats are unrestricted; targeted non-inherited stats contribute 1/32 each. This is an **approximate per-egg IV estimate**, ignoring small RNG modulo bias and correlations. It excludes shiny/nature/gender/ability filters. Compatibility affects parent tie-breaking, but generation skips the waiting time it normally controls.

Shininess never contributes to parent selection. FR/LG has no shiny-parent bonus, Masuda bonus, Destiny Knot effect or inherited Everstone nature in this implementation. Two six-perfect parents still have approximately **1/32,768** odds of a six-perfect egg. Combining that with shiny gives roughly **1/268 million** before further filters; demanding combinations can take a long time and have no guaranteed completion time. A displayed limit means the search stopped without a match, not that your target is impossible.

## Beta limitations

- Tested on the installed **0.3.21** payload and upstream `dev` commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`. It relies on internal APIs because those are the current FR/LG breeding interfaces.
- Standard imported FR/LG data was tested. Mods that change species data, breeding, storage or native menus may change behavior.
- PKHeX validation now covers every compatible parent species in the imported data, both editions, eggs and hatchlings, both PID parities for six-perfect Charmander, shiny trainer-identity cases, and Pokémon read from complete exported `.sav` files. All samples pass. See `TEST-REPORT.md` for counts and the tested checker version. Custom ROM data and mods that change breeding are outside this validation; finite regression testing cannot certify all external changes.
- Automated engine and UI/controller tests were run against the actual release Lua modules and imported data. Screens were visually checked by rendering the real drawing operations with imported game fonts, frames and sprites. A full interactive playthrough was not performed; a separate native visual-test process was terminated by macOS before opening.
- No real save files or installed game/mod files were edited during development/testing.

See `TEST-REPORT.md` for evidence and `tests/` for reproducible tests.

## Source and tests

`main.lua` registers the start-menu and input hooks. `breeder.lua` owns generation, selection, repair, search and delivery. `export.lua` saves/exports in-game and corrects OT-name formatting only for marked Auto Breeder results. `screen.lua` owns navigation and controls. `view.lua` draws the LegalMon-style screens. The source ZIP includes integration, UI, export lifecycle, broad export-matrix tests and a PKHeX checker.

From a Gen1Recomp source checkout containing its test suite, with LuaJIT available:

```sh
export AUTOBREEDER_ROOT=/absolute/path/to/autobreeder
export AUTOBREEDER_CACHE=/absolute/path/to/firered/data/generated/gba
export AUTOBREEDER_GAME=firered
export LUA_PATH='./?.lua;./?/init.lua;;'
luajit "$AUTOBREEDER_ROOT/tests/integration.lua"
luajit "$AUTOBREEDER_ROOT/tests/ui.lua"
```

Repeat integration with the LeafGreen cache and `AUTOBREEDER_GAME=leafgreen`. Both caches must already have been imported by the game. Tests create isolated in-memory sessions and do not access player save files. Optional `AUTOBREEDER_PK3=/existing/output/directory` writes sample encrypted `.pk3` files and a complete synthetic `.sav` for separate validation. The UI suite uses a FireRed test session and should use the FireRed cache.

To reproduce the full legality matrix, set `AUTOBREEDER_PK3` to an empty directory and run `tests/legality_matrix.lua` for each edition. Build `tests/LegalityCheck/LegalityCheck.csproj` with .NET 10 and `-p:PKHeXCorePath=/absolute/path/to/PKHeX.Core.dll`, then run its output DLL with one or more sample directories as arguments. It checks both encrypted `.pk3` files and the party/PC Pokémon directly inside `.sav` files. PKHeX is an external test dependency, not bundled in the mod.

Engine reference: https://github.com/bryanthaboi/gen1recomp/tree/84e076b2d1e2dda36073ff55ec7c311a6b97519c/src/core/game3

For the export lifecycle regression, set `AUTOBREEDER_PK3` to an existing scratch directory and run `tests/export_lifecycle.lua` for each edition. It intentionally writes both `*_launcher_unpatched.sav` negative controls and `*_ingame_corrected.sav` passing files. Validate those groups separately: the former must reproduce the egg terminator error. Persistence and filesystem calls are mocked; native save schema, serialization and GBA export code are used.


## Screenshot gallery

Native UI renders from development, using fixture/demo state. Some images predate later menu additions; see the feature documentation above for the current release.

### Home

Historical preview (older build): [autobreeder-home](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/autobreeder-home.png).

### Ivs

Historical preview (older build): [autobreeder-ivs](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/autobreeder-ivs.png).

### Keep

Historical preview (older build): [autobreeder-keep](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/autobreeder-keep.png).

### Progress

Historical preview (older build): [autobreeder-progress](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/autobreeder-progress.png).

### Result

Historical preview (older build): [autobreeder-result](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/autobreeder-result.png).

### Targets

Historical preview (older build): [autobreeder-targets](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/autobreeder-targets.png).

### Emerald source port (1.1.0)

Requires Gen1Recomp 0.3.39. Emerald uses its native pending personality generator, IV inheritance, Everstone nature inheritance, Light Ball/Volt Tackle inheritance and hatch locations. Searches preserve all three live RNG states. The export name-padding correction is installed on the active game's codec.

The three native integration runs pass: 175 checks each for FireRed and LeafGreen, 178 for Emerald. They compare generated eggs with the engine, exercise searches and parent replacement, and round-trip party/PC data through cartridge saves. Emerald tests also cover Light Ball and Everstone behavior. This is automated validation, not a new manual playtest or complete PKHeX certification.

The collection's distributed ZIPs remain on the previous versions while the broader Emerald port is in progress.
