# Shiny Hunter 0.1.4 — FireRed / LeafGreen

An automatic encounter hunter for gen1recomp, with the same blue header, native FRLG frames, sprite panel, six-entry home menu and controller navigation as LegalMon. This is an initial tested build, not a claim that every story encounter has been individually certified.

Based on the Pokemon Gen 1 Recompilation Project by BOIS CLUB GAMES, LLC
(https://github.com/bryanthaboi/gen1recomp).

## Install and start

Import `shiny-hunter-0.1.4.zip` using gen1recomp's mod manager, enable **Shiny Hunter** for FireRed or LeafGreen, and restart the game if requested. Alternatively, place the extracted `shiny_hunter` directory containing `manifest.json` inside your gen1recomp mods directory. No ROM data is included; the UI reads your game's existing imported assets. LegalMon is not a dependency.

Open **START → SHINY HUNTER**. Choose **Encounter modes**, then **Configure hunt** if you want additional filters. Stand at your starting position and choose **Start hunt → Start selected mode**.

- **Walk left/right or up/down:** stand in a clear patch of grass, cave floor or surfable water. The game performs normal movement and encounter rolls. Adjust the stride in Settings to fit the space.
- **Static / gift: interact:** face the target before starting. The hunter repeats A. Use a recorded route when dialogue needs anything other than repeated A.
- **Fishing:** register an owned rod, face fishable water, then start. It uses the registered-item input and handles result dialogue.
- **Recorded route:** choose **Start hunt → Record new route**, then play one attempt yourself. Recording ends automatically as soon as the hunter sees a generated battle opponent, received gift/egg, or newly initialized roamer. If it is not a protected shiny, the starting point is restored and your input sequence repeats unattended. Record a fresh route for a different target.

**START or F10 pauses automation.** B/L goes back inside the hunter. Closing the screen leaves a paused hunt paused. Choose Resume hunt to continue, or **Hunt controls → Keep result & stop** to finish. Normal game saving remains your responsibility after keeping a result.

## How it works

The hunter snapshots your current settled overworld state and stores a recovery copy in its playthrough-specific mod storage. Each rejected attempt uses the engine's soft-reset and continue paths to restore that state in memory. Party, PC, money, items and story flags rewind with it. Surf/bicycle state and Safari balls, steps and flags are also restored. The current RNG stream carries forward and the engine applies its normal continue perturbation; it does not reload an identical RNG seed every attempt.

The hunter does not alter generated PIDs or IVs, force shiny results, bypass encounter tables, or inject a found Pokemon into storage. It follows this recompilation's generation logic and current mods; it does not claim cartridge-perfect RNG behaviour or perform a separate legality proof. Other enabled mods can affect odds and encounters.

For wild battles it checks the PID against your trainer IDs, which the engine uses on capture. Missing OT fields on a wild battler are filled with those same IDs so the native sprite agrees with the check. Gifts and eggs use their own OT fields. Fixed or foreign-trainer gifts pause the run.

Automatic attempts reset rather than fighting or fleeing from each unwanted encounter. This means walking steps, egg progress, consumed resources and other progress after the starting point are discarded on failed attempts, just as with resetting. Start before the Pokemon is generated. Rehatching an existing egg or reencountering an already generated roamer does not give a new PID.

## Protection and capture

By default **any shiny stops the hunt**, including one that fails your species/nature/IV filters. Keep this protection enabled unless you deliberately want to discard other shinies. Settings requires an explicit choice before turning protection off.

The optional auto-catch mode submits normal ball-use actions with your selected ball; Safari encounters use Safari Balls. It consumes inventory and obeys normal capture results. It does not attack, heal, switch, prevent fleeing, or guarantee a capture. Depleted balls, full storage, a fainted lead, unexpected menus or a capture timeout return control to you. After a catch or failed capture, it never starts another hunt automatically.

The hunter freezes the game while its menu is open. It releases its input holds when paused/stopped. Hunt speed is temporarily applied only inside an active update, preserving your game speed settings. Normal SAVE is blocked while automation is running, so a failed attempt cannot accidentally become your ordinary save.

Found history contains metadata for the latest 100 shinies, not extra Pokemon. Settings and history persist through mod storage. A crash does not preserve a live battle; the hunter does not claim battle savestate support. **Settings → Recover last starting point** can restore the last stored starting point in memory for the same trainer/playthrough; the confirmation explains that later unsaved progress is discarded. Input routes and active runs are session-only and must be recorded again after restarting the application.

## Encounter coverage

| Encounter | Method | Verification in this build |
|---|---|---|
| Wild land / cave | Automatic walking | Real cave walking and natural rolls tested in both games |
| Surfing | Automatic walking while already surfing | Real water terrain and repeated encounters tested in both games |
| Fishing | Registered rod | Real Pallet Town shoreline fishing tested in both games |
| Static encounters | Interact or recorded route | Real Power Plant script, resets and replay tested in both games |
| Starters / gifts / fossils / Game Corner | Recorded route, sometimes Interact | Gift factory and detection tested; individual story routes not exhaustively tested |
| Daycare / gift eggs | Record before new egg creation or collection | Egg factory/detection tested; existing eggs are ignored |
| Rock Smash | Record interaction from before the rock | Generic replay path; individual rock scripts not tested |
| Safari Zone | Walk / recorded route | Real Safari terrain, counters and repeated encounters tested; capture/flee outcomes not exhaustively tested |
| Roamers | Record their initial release | New-roamer detection and existing-roamer guard tested at controller level; full release story route not tested |
| Fixed in-game trades / event imports | Excluded | Foreign-trainer gifts stop automation |

For long scripts, increase the attempt timeout. A recorded route is timing-based: NPC movement, branching dialogue and an unexpected screen can require re-recording. It is not autonomous navigation to arbitrary targets around the world. When no generation occurs, the hunter times out instead of silently claiming attempts.

## Compatibility and testing

Verified against an isolated copy of your installed **gen1recomp 0.3.21 update payload**, in both games, as well as development commit `fab224458f9d5af79a82b5ff5338347ef74c0189`, mod API 2. It uses engine internals; other versions may need an adapter update. It adds a separate menu entry without changing LegalMon. Simultaneous automation mods must not drive the same game at once.

Tests include 72 controller assertions, real engine integration with both imported FRLG datasets, production mod-loader/sandbox/storage/input-hook tests, native UI render inspection, manifest validation and ROM-content lint. Tests use a headless LÖVE shim; this is not a claim of desktop/controller end-to-end QA on every device. See `TESTING.md` in the source package for reproducible commands.

## Changes in 0.1.3

- Hunt speed options now include **16×, 32×, 64×, 128× and 256×**, alongside 1×–8×. New configurations default to **64×**. Existing saved settings are retained: pause, open **Settings → Speed**, select **256×**, then resume for the fastest target.
- The engine still checks every simulation tick. A failed attempt ends the current burst immediately before the next frame resets it; shiny detection or a pause also ends the burst. Recording stays at 1×.
- Multipliers are targets, limited by CPU speed, the engine's per-frame work budget and reset overhead. No skipped encounter checks or changed shiny odds. The engine's work budget stays enabled.
- Both games passed 100 consecutive static encounters at each of 8×, 64× and 256×, plus another 100 at 256× with a real CPU clock driving the work budget. Protected-shiny, START-before-reset and frozen-menu checks passed at every tested speed.

## Changes in 0.1.2

- START now pauses before any queued reset, preserving the current encounter.
- New acquisitions are counted even when their species, personality and trainer IDs match an existing Pokemon. Moving an existing Pokemon between party and PC does not create an attempt.
- Added regression tests for both fixes and exercised production hooks at 8× speed.

## Changes in 0.1.1

- Fixed reset losing Surf/bicycle state and exiting Safari mode. Snapshot format 2 includes these runtime fields; create a new starting point after updating.
- Preserved rapid input presses in recorded routes, including a press/release inside one game tick.
- Prioritized a matching shiny when multiple Pokemon arrive together and protection of other shinies is disabled.
- Kept missing-identity/unsupported-generation checks active after resuming.
- Stopped auto-capture immediately if the lead faints, before it can drive a replacement menu.
- Scoped the capture timeout to the current battle and restored the configured hunt speed after recording.
- Raised the minimum engine version to the installed/tested 0.3.21 release.

## Screenshot gallery

Native UI renders from development, using fixture/demo state. Some images predate later menu additions; see the feature documentation above for the current release.

### Filters

![shiny-hunter-filters](../../docs/screenshots/shiny-hunter-filters.png)

### Found

![shiny-hunter-found](../../docs/screenshots/shiny-hunter-found.png)

### Home

![shiny-hunter-home](../../docs/screenshots/shiny-hunter-home.png)

### Modes

![shiny-hunter-modes](../../docs/screenshots/shiny-hunter-modes.png)

### Settings

![shiny-hunter-settings](../../docs/screenshots/shiny-hunter-settings.png)

### Speeds

![shiny-hunter-speeds](../../docs/screenshots/shiny-hunter-speeds.png)

## 0.1.4 dual-screen integration

Adds explicit detached editor ownership for FRLG Dual Screen 0.2.0. While its live editor is active, native field updates and controller input continue; menu input comes from companion touch. Active automation retains its own rules. Exposes busy state so the companion refuses targeted encounters while a hunt snapshot or automation is active. Standalone behavior is unchanged.


## Native Pokémon legality corrections — 0.1.5

This release includes the shared FRLG generation/export corrections. It sets valid ability slots for newly generated/caught Pokémon, creates native gift eggs with the correct egg metadata, preserves fixed NPC-trade identity and contest values, and generates new roamers with retail FRLG PID/IV correlations. The roaming beast's stored personality and IVs now reach the battle without being regenerated. Native unhatched eggs receive the required OT-name padding during in-game export.

The same helper is bundled independently with Dual Screen, Shiny Hunter, Encounter Reset, Encounter Tour, Day Care Viewer and Pokémon Services. No additional mod is required. Co-loading these packages applies the corrections once; disabling every participating mod or unloading the game stops the wrappers. Existing Pokémon are not rerolled or bulk-repaired.

**For a cartridge save, use MODS → this mod → SAVE + EXPORT while in the field.** This first saves the active game and then exports with the egg-name correction loaded. The log gives the output path under `exports/<edition>/`. A fresh launcher export can still use the host's unpatched egg-name encoder; copy the in-game export directly. Restart after installing updates.

See the collection's `docs/LEGALITY-FIXES.md` for the regression results and limits. This corrects the identified defects; a passing sample matrix does not certify every possible modified ROM, species combination or future host release.
