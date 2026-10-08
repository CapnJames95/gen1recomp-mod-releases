# Shiny Hunter 0.3.4

## Changes since public v0.3.0

Support for **all five Gen 3 games — Ruby, Sapphire, Emerald, FireRed and LeafGreen — is here**. Extends shiny odds to static encounters, new starters, gifts, eggs and roamers. Adds an optional Dual Screen odds toggle and hold-L shiny shortcut for Wild Pokémon encounters. Fixed events and existing Pokémon remain unchanged.


<!-- RS-COMPATIBILITY -->
## Ruby and Sapphire compatibility

Ruby and Sapphire use their native encounter-generation path for shiny odds and hunting, preserving native PID/IV generation instead of rolling IVs a second time. Automated export legality checks passed for the tested specimens; hardware gameplay still needs verification.

Validated with gen1recomp **0.3.56 (Mac) / 0.3.57 (Android)**. Automated checks do not replace exhaustive gameplay testing.
<!-- /RS-COMPATIBILITY -->

[Download latest release](https://github.com/CapnJames95/gen1recomp-shiny-hunter/releases/latest) · [Report an issue](https://github.com/CapnJames95/gen1recomp-shiny-hunter/issues)

> **AI development disclaimer:** Developed with OpenAI Codex assistance. Automated tests do not guarantee correctness; keep save backups.

## New in 0.3.4

**Hold L while starting an encounter in Dual Screen’s Wild Pokémon screen** to request a shiny for that encounter. This works even with Dual Screen odds OFF or normal odds set to Vanilla. Release L for the usual behavior; your saved odds and toggle are never changed. Requires Gen3DualScreen 0.4.16+ and Shiny Hunter enabled. Uses complete encounter rerolls and retains the normal encounter exclusions.

## New in 0.3.3

When Gen3DualScreen is loaded, **START → SHINY HUNTER → Dual Screen odds** appears. Toggle it **ON** to apply your selected **Shiny odds** to the Wild Pokémon button and its individual encounter tiles. It defaults to **OFF**, changes inline, and is remembered when you save normally. It does not start an automatic hunt or change the selected species/level. Stop an active hunt before changing it. Requires Gen3DualScreen 0.4.15 or newer; older versions lack this integration.

At 1/1, 500 generated/captured button-style encounters across FR/LG/E/R/S were all shiny and passed PKHeX. Other encounter-generation mods retain their exclusions.

## New in 0.3.2

The odds setting now also covers newly generated starters, ordinary gifts, gift eggs, daycare eggs and roamers across FR/LG/E/R/S. Fixed NPC trades, fixed event specimens and shiny locks are not overridden. Event Distributions and LegalMon retain their own explicit shiny controls.

Set the odds **before receiving a gift or starting a roamer’s story event**. Existing roamers retain their identity; meeting one again does not reroll it. For eggs, set odds **before breeding**: Emerald chooses the PID when the daycare produces the egg; FR/LG/R/S finish it at pickup. Existing eggs are unchanged, and hatching never rerolls them. Parent IV/move inheritance and native Emerald Everstone generation remain in use. The guaranteed setting can briefly pause while searching.

Automated checks: 500 shiny starter/gift/roamer/hatched-egg exports across all five games passed PKHeX, alongside the 520 stationary samples below. Finite odds still use approximate extra-roll rates; analyzer acceptance is not a proof of every possible build or cartridge RNG history.

## New in 0.3.0

- Optional wild shiny odds from 1/4096 down to 1/2, plus 1/1 for supported encounters. Vanilla 1/8192 remains the default.
- Continuous walking/fishing catches: enable **On match: Auto-catch** and **After catch: Keep hunting** in Settings. Each catch is kept before returning to the starting spot.
- Native engine repeat-capture tests pass in FR/LG/Emerald. Generated shiny samples passed PKHeX; see scope and limitations below.


Previous public-build preview (does not show the new Wild shiny odds option; Dual Screen is optional):

![Current shiny-hunter menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-shiny_hunter.png)


An automatic encounter hunter for gen1recomp, with the same blue header, native FRLG frames, sprite panel, home menu and controller navigation as LegalMon. This is an initial tested build, not a claim that every story encounter has been individually certified.

Based on the Pokemon Gen 1 Recompilation Project by BOIS CLUB GAMES, LLC
(https://github.com/bryanthaboi/gen1recomp).

## New in 0.3.1

Shiny odds now apply to standard scripted stationary encounters across FR/LG/E/R/S. Automated battle/capture tests generated 520 guaranteed-shiny legendary/static samples; all 520 passed PKHeX, including Rayquaza in Ruby. This is automated verification, not manual hardware testing. Existing Pokémon are not changed; new roamer support was added in 0.3.2.

## Shiny odds — wild and stationary

Requires **gen1recomp 0.3.42+**. Open **START → SHINY HUNTER → Shiny odds**. Default: **Vanilla (1/8192)**. Optional approximate rates: **1/4096, 1/2048, 1/1024, 1/512, 1/256, 1/128, 1/64, 1/32, 1/16, 1/8, 1/4, 1/2**. **1/1** searches until it finds a naturally shiny candidate for a supported encounter. Save normally to remember the setting for that save. Automatic hunting does not need to be running. Stop an active hunt before changing odds.

The original encounter still selects the species and level. Extra complete personality/IV candidates are generated before battle; the first shiny is kept, or the original candidate if none succeeds. The shiny threshold, trainer IDs and existing Pokémon are unchanged. Rates are approximate because the setting is a bounded number of correlated RNG trials, not an independent exact-probability switch. The approximate settings use up to 5,678 candidates per encounter at 1/2. The 1/1 setting has no attempt cap and stops only on a shiny candidate. Higher rates can cause a short pause before battle, especially 1/1; they do not speed up the search by editing a Pokémon’s PID or IVs. Emerald candidates use the native nature/Cute Charm/Synchronize path.

**Scope:** ordinary grass/cave/surf encounters, fishing, Rock Smash, Sweet Scent and fresh standard stationary encounters, including Ruby’s Rayquaza. Static encounters reroll complete Method 1 PID/IV pairs; their species, level and held item remain unchanged. Set the odds before interacting with the Pokémon. Newly generated starters, gifts, eggs and roamers are also supported as described above. **Excluded:** fixed event distributions, fixed NPC trades, Unown wild encounters, Safari and Battle Frontier, prebuilt encounters, and encounters replaced through another mod's encounter-roll/species hook. This is a first prototype, not full encounter coverage or a cartridge-RNG-history guarantee. It skips excluded cases rather than forcing their shininess.

**Validation:** 50,000 synthetic encounter attempts through the generation code, including normal FR/LG/Emerald and Emerald Synchronize/Cute Charm leads, at the ~1/64 setting. Each group of 10,000 produced 154–170 shinies. All **807 exported shiny catches passed PKHeX**, using the real battle constructor and capture path. Save/reload of settings, no-op vanilla mode, exclusions, wrapper nesting/reload/disable and failure cleanup have regression coverage. Measured generation maxima were under 3 ms on this Mac in the headless fixture; this is not a Thor gameplay-performance measurement. This sample covers Route 1 Pidgey and Route 101 Zigzagoon and does not prove every encounter slot or species legal.

**Lower-rate validation:** 7,680 additional attempts across all six new settings, FR/LG/Emerald and Emerald Synchronize/Cute Charm leads. All 1,280 attempts at 1/1 were shiny. All 2,465 exported shiny catches passed PKHeX. The longest measured generation call was 0.221 seconds on this Mac (1/1 with Cute Charm); this is not a maximum-time guarantee or a Thor performance measurement. The same species/route coverage limits apply. Menu selection, finite search budgets and a guaranteed search beyond the largest finite budget also passed regression checks.

Inspired by [KiraPatch](https://github.com/eightmouse/KiraPatch)'s approach of retaining genuine shiny generation rather than changing the shiny threshold. Implemented in Lua for gen1recomp; no ROM patch is applied.

## Three-game development update

The previous public build required gen1recomp 0.3.39 or newer. Shiny Hunter 0.3.0 requires 0.3.42+. Emerald uses its native encounters and preserves underwater state and Mach/Acro Bike type across attempt resets. Active Battle Frontier challenges are blocked. Existing FRLG roaming-Pokémon legality corrections remain restricted to FRLG; Emerald keeps its full native IVs.

Automated tests exercise native encounter generation, recorded routes, fishing, Surf/Safari recovery, menu integration and normal ball capture. Manual Emerald device testing is still pending; automated coverage does not replace hardware gameplay validation.

0.2.1 adds a direct menu entrypoint for Hoenn Tools’ Feebas assistant. It opens the hunter without starting automation or altering your configuration. Requires gen1recomp 0.3.39. The older FR/LG-specific test descriptions below are historical coverage; current native integration tests run in all three games.

## Install and start

Import `shiny_hunter-0.3.0.zip` using gen1recomp's mod manager, enable **Shiny Hunter** for FireRed, LeafGreen or Emerald, and restart the game if requested. Alternatively, place the extracted `shiny_hunter` directory containing `manifest.json` inside your gen1recomp mods directory. No ROM data is included; the UI reads your game's existing imported assets. LegalMon is not a dependency.

Open **START → SHINY HUNTER**. Choose **Encounter modes**, then **Configure hunt** if you want additional filters. Stand at your starting position and choose **Start hunt → Start selected mode**.

- **Walk left/right or up/down:** stand in a clear patch of grass, cave floor or surfable water. The game performs normal movement and encounter rolls. Adjust the stride in Settings to fit the space.
- **Static / gift: interact:** face the target before starting. The hunter repeats A. Use a recorded route when dialogue needs anything other than repeated A.
- **Fishing:** register an owned rod, face fishable water, then start. It uses the registered-item input and handles result dialogue.
- **Recorded route:** choose **Start hunt → Record new route**, then play one attempt yourself. Recording ends automatically as soon as the hunter sees a generated battle opponent, received gift/egg, or newly initialized roamer. If it is not a protected shiny, the starting point is restored and your input sequence repeats unattended. Record a fresh route for a different target.

**START or F10 pauses automation.** B/L goes back inside the hunter. Closing the screen leaves a paused hunt paused. Choose Resume hunt to continue, or **Hunt controls → Keep result & stop** to finish. Normal game saving remains your responsibility after keeping a result.

## Continuous shiny catching

Set **Settings → On match: Auto-catch**, choose your ball, then set **After catch: Keep hunting**. Select walking or fishing and start from the spot you want to reuse. Fishing stays at the same spot; walking uses the configured short stride and returns to its starting tile after each catch. This also works with the optional shiny-odds settings.

After a successful capture, the hunter waits for field control, refreshes its recovery checkpoint with the caught Pokémon, remaining balls, HP and current progress, then returns to the original position on the same map. Later rejected encounters reset to this refreshed checkpoint, preserving previous catches. It stops if storage is full, balls are depleted, the lead faints, the map changes, field control fails to return, or checkpoint creation fails. Protected shinies outside your filters still stop for your attention. START/F10 pauses; stop and save normally to keep your catches in your ordinary save file. There is no automatic normal-save overwrite.

Controller regression tests cover consecutive catches, preserving catches and ball usage through subsequent resets, pause/resume, unsupported modes, and checkpoint/storage/map/timeout failures. Native engine integration tests also passed in FireRed, LeafGreen and Emerald: two consecutive catches survived checkpoint restores and balls remained consumed. Hardware gameplay validation is pending.

## How it works

The hunter snapshots your current settled overworld state and stores a recovery copy in its playthrough-specific mod storage. Each rejected attempt uses the engine's soft-reset and continue paths to restore that state in memory. Party, PC, money, items and story flags rewind with it. Surf/bicycle state and Safari balls, steps and flags are also restored. The current RNG stream carries forward and the engine applies its normal continue perturbation; it does not reload an identical RNG seed every attempt.

With **Shiny odds: Vanilla**, the automatic hunter does not alter generated PIDs or IVs, force shiny results, bypass encounter tables, or inject a found Pokemon into storage. The optional odds prototype generates extra complete wild candidates before battle, as described above. It follows this recompilation's generation logic and current mods; it does not claim cartridge-perfect RNG behaviour or perform a separate legality proof. Other enabled mods can affect odds and encounters.

For wild battles it checks the PID against your trainer IDs, which the engine uses on capture. Missing OT fields on a wild battler are filled with those same IDs so the native sprite agrees with the check. Gifts and eggs use their own OT fields. Fixed or foreign-trainer gifts pause the run.

Automatic attempts reset rather than fighting or fleeing from each unwanted encounter. This means walking steps, egg progress, consumed resources and other progress after the starting point are discarded on failed attempts, just as with resetting. Start before the Pokemon is generated. Rehatching an existing egg or reencountering an already generated roamer does not give a new PID.

## Protection and capture

By default **any shiny stops the hunt**, including one that fails your species/nature/IV filters. Keep this protection enabled unless you deliberately want to discard other shinies. Settings requires an explicit choice before turning protection off.

The optional auto-catch mode submits normal ball-use actions with your selected ball; Safari encounters use Safari Balls. It consumes inventory and obeys normal capture results. It does not attack, heal, switch, prevent fleeing, or guarantee a capture. Depleted balls, full storage, a fainted lead, unexpected menus or a capture timeout return control to you. By default it stops after a catch. With **Settings → On match: Auto-catch** and **After catch: Keep hunting**, walking and fishing hunts resume automatically after successful catches. Repeat catching is off by default and does not support recorded routes, interactions, Safari or roamers. Failed captures and unexpected battle endings always stop.

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

Historical preview (older build): [shiny-hunter-filters](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/shiny-hunter-filters.png).

### Found

Historical preview (older build): [shiny-hunter-found](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/shiny-hunter-found.png).

### Home

Historical preview (older build): [shiny-hunter-home](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/shiny-hunter-home.png).

### Modes

Historical preview (older build): [shiny-hunter-modes](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/shiny-hunter-modes.png).

### Settings

Historical preview (older build): [shiny-hunter-settings](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/shiny-hunter-settings.png).

### Speeds

Historical preview (older build): [shiny-hunter-speeds](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/shiny-hunter-speeds.png).

## 0.1.4 dual-screen integration

Adds explicit detached editor ownership for Gen3DualScreen 0.2.0. While its live editor is active, native field updates and controller input continue; menu input comes from companion touch. Active automation retains its own rules. Exposes busy state so the companion refuses targeted encounters while a hunt snapshot or automation is active. Standalone behavior is unchanged.


## Native Pokémon legality corrections — 0.1.5

This release includes the shared FRLG generation/export corrections. It sets valid ability slots for newly generated/caught Pokémon, creates native gift eggs with the correct egg metadata, preserves fixed NPC-trade identity and contest values, and generates new roamers with retail FRLG PID/IV correlations. The roaming beast's stored personality and IVs now reach the battle without being regenerated. Native unhatched eggs receive the required OT-name padding during in-game export.

The same helper is bundled independently with Dual Screen, Shiny Hunter, Encounter Reset, Encounter Tour, Day Care Viewer and Pokémon Services. No additional mod is required. Co-loading these packages applies the corrections once; disabling every participating mod or unloading the game stops the wrappers. Existing Pokémon are not rerolled or bulk-repaired.

**For a cartridge save, use MODS → this mod → SAVE + EXPORT while in the field.** This first saves the active game and then exports with the egg-name correction loaded. The log gives the output path under `exports/<edition>/`. A fresh launcher export can still use the host's unpatched egg-name encoder; copy the in-game export directly. Restart after installing updates.

See the collection's `docs/LEGALITY-FIXES.md` for the regression results and limits. This corrects the identified defects; a passing sample matrix does not certify every possible modified ROM, species combination or future host release.
