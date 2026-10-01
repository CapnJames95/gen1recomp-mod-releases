# LegalMon 0.18.1

Current companion preview (synthetic Emerald session; Dual Screen is optional):

![Current legalmon menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-legalmon.png)


**Frontier safeguard:** receiving generated Pokémon (including improved breeding parents) is blocked during an active Emerald Battle Frontier challenge. Pending results and event receipts are left unchanged.

## New in 0.18.0

Adds active Emerald support alongside FireRed and LeafGreen on gen1recomp 0.3.39. Emerald uses its native species mapping, all 30 tutor compatibility bits, game-specific encounter profiles and a separate Emerald egg RNG/inheritance proof. Light Ball / Volt Tackle breeding is available where the proof supports it. Imported or historical FireRed/LeafGreen origins remain those games' origins; they are not relabelled as Emerald. Unown forms in Emerald use proven FireRed transfer origins.

Emerald validation: 17,798 native-data checks across all 386 species, 512 native egg replay checks, and 10,143 exported samples accepted by PKHeX. These are synthetic automated tests, not a guarantee that every requested build is possible or a substitute for manual playtesting. Bounded searches and incomplete ancestry proofs still fail closed. Thorough manual gameplay validation remains pending.

The current download includes this three-game port. The older change history below describes earlier FRLG releases.

LegalMon adds a native-style FireRed/LeafGreen/Emerald start-menu screen with generating paths for **all 386 Gen III species**. Configure a build, validate its acquisition-specific RNG constraints, review its sprite and exact result, then explicitly send it to party or PC. Version 0.4.0 adds breeding, special evolutions, roamers, Unown A and restricted event origins. All species does not mean every conceivable origin, form or exact build.

Based on the Pokemon Gen 1 Recompilation Project by BOIS CLUB GAMES, LLC.

Trainer ID and Secret ID use a digits-only keypad (0–65535), with DEL and OK. Both controller and physical number-pad input work. OT names and searches retain the letter keyboard.

### 0.17.0: teaching on the evolution level-up

For supported ordinary level/friendship evolution paths, a Pokemon can now learn a level-up move on the same level-up that triggers evolution. The proof separates the level at which the earlier species must already exist from its final level-up teaching cutoff. This also works inside breeding-parent histories and can avoid incorrectly requiring level 101.

Every level-up evolution still requires a real level gain. Two consecutive level-up evolutions cannot be collapsed into one, and a Pokemon captured at its evolution level must gain another level. Earlier TM/tutor teaching stays before the evolution-triggering level-up; stone/trade paths can teach and evolve at the same level. Reports show this order and delivery rechecks the teaching cutoff. Special evolution methods remain outside this move-history model.

### 0.16.0: pre-evolution machines and tutors

The move picker and validator now include FRLG TM/HM and supported tutor moves that only an earlier evolutionary stage can learn. Each teaching step must fit the same acquisition-bound timeline as earlier-stage level-up moves; an already-evolved capture cannot claim that it learned a move before capture.

This also applies inside breeding-parent chains: a parent may retain an ancestral machine/tutor move alongside inherited and later-learned moves. Reports distinguish TM/HM, tutor and level-up sources. Delivery reloads ancestral compatibility and rejects stale or modified proofs. No compatibility tables are bundled, and generation does not consume TMs or one-use tutor flags.

Ordinary level, friendship, stone and trade evolution timelines are supported, including evolution-level teaching added in 0.17.0. Special evolution methods remain conservative and return incomplete when unproven. Parent PID/IV genealogy and the other coverage gaps are unchanged.

### 0.15.0: chained parent moves and witnessed Sketch

Egg validation now searches parent move histories recursively when direct inheritance is insufficient. It proves the entire required move combination on one father, and the required shared moves on one mother, at each generation. A parent can first inherit moves, retain supported pre-evolution level-up moves, then learn its final-species moves. Cycles with no real move source cannot invent a move. The explanation lists the parent-chain stages; delivery rebuilds the ancestry and refuses stale or altered sources.

Smeargle can supply supported inherited moves through Sketch when the imported catalog contains another species with a direct FRLG level-up/reminder, TM/HM or tutor source for that move. Each Sketch source names its witness species. This is parent-move support, not a new unrestricted Smeargle move generator. Sketch battle setups for Mimic, Metronome, Mirror Move, Selfdestruct, Transform, Explosion, Sleep Talk and Memento remain deliberately excluded; Struggle and Sketch cannot be copied. Missing witnesses also remain unsupported.

Searches stop at 2,048 evaluated parent states or 16 ancestry levels. They return **incomplete** if no supported proof is found, not global impossibility; they do not promise the shortest chain. Parents and battle witnesses are hypothetical, not owned or consumed Pokemon. **Move ancestry is now modeled, but recursive parental PID/IV ancestry is still not reconstructed.** Other source-game breeding algorithms and missing evolution/move histories remain documented coverage gaps.

### 0.14.0: both-parent inheritance and special parents

With **Configure → Pokemon → Acquisition → egg**, the move picker also offers the offspring's later level-up moves as potential shared-parent inheritance. Validation requires both parents to know those moves, while one father must also supply every requested egg-list move. It never combines different fathers or assumes Ditto can provide a missing move.

Nidoran male and Volbeat can now inherit through their female counterparts. Direct-source Ditto breeding is supported with a breedable male/genderless parent from the offspring's own evolution family; for example, Tyrogue can inherit a move directly learned by a compatible Hitmon evolution. Existing offspring PID constraints remain enforced. Incense routes retain their existing item requirements.

Reports identify both parent slots and explain maternal move sources. Delivery reconstructs both parents' sources before accepting a result. Version 0.15.0 extends this with bounded chains, supported pre-evolution parental moves and witnessed Sketch. Parents remain hypothetical; recursive PID/IV ancestry and breeding variants beyond the implemented FRLG/Emerald models are not yet proven. Unsupported cases stay **incomplete**, never silently relaxed.

### 0.13.0: compatible egg-move combinations

Choose **Configure → Pokemon → Acquisition → egg**, then select moves and validate. The move picker reads `pokemon/egg_moves.lua` from your own imported ROM cache; re-import if this optional cache is missing. Missing data never invents an egg move.

Every move needing inheritance must fit on **one compatible male father's four-move set**, learned directly through that father's FRLG level-up/reminder, TM/HM or supported tutor sources. Validation does not combine incompatible fathers. The legality report names the hypothetical father species and each move's source; delivery rebuilds this proof from the trusted catalog. Egg moves can be retained through supported offspring evolutions.

Direct-source Ditto and shared-parent inheritance were added in 0.14.0; bounded parent chains and witnessed Sketch were added in 0.15.0. A listed move is not a promise that every combination can be proven: unsupported combinations report **incomplete**, with no silent substitution. Parents are hypothetical and are not consumed from your save. Offspring egg PID/IV constraints remain independently checked; recursive parent PID/IV ancestry remains unmodeled.

### 0.12.0: proven pre-evolution moves

The move picker now includes earlier-stage FRLG level-up/reminder moves from eligible acquisition paths. Validation binds all requested moves to one path and records when each ancestor can be trained and evolved; it does not merely union every ancestor's learnset. The report lists the teaching/evolution stages. Delivery reconstructs the sequence from the trusted current catalog and rejects stale or modified histories.

Supported chains use ordinary level, friendship, stone and trade evolutions. Each level-up transition needs a distinct level gain, but level-up moves can be taught before evolution on that same gain. Stone/trade transitions can stay at the same level. Special evolution chains remain unmodeled; earlier-stage TM/tutor support was added in 0.16.0. If an earlier-stage move needs an unmodeled sequence, the result is **incomplete**, not a claim of global impossibility. Already-evolved acquisitions cannot borrow a teaching history from before capture.

### 0.11.0: imported FRLG NPC trades

Choose **Configure → Pokemon → Acquisition → trade** and your active FRLG origin to generate an imported NPC trade record. All nine active-edition trades and supported evolutions are included. Nickname, original trainer, PID, IVs, ability slot and contest conditions come from `trades/ingame_trades.lua` in your own ROM cache; no NPC trade database is bundled.

These are fixed records, not RNG spreads. Validation checks one immutable PID/IV result per profile; incompatible exact nature, gender, ability, shiny or IV requests fail. Custom OT replacement is refused. The explanation explicitly identifies the fixed record rather than claiming an RNG seed. Delivery reloads the trusted catalog to reject changed records or constraints.

The met level uses the lowest supported acquisition level of the requested offered species, with later training/evolution allowed. This does not enumerate every possible trade met level or prove you own an offered Pokemon. Generation does not remove a party Pokemon or consume trade flags; held items and mail are omitted, as they can legitimately be removed after trading. Only the active edition's imported NPC records are offered. Re-import if the trade cache is missing; unsupported or malformed records fail closed.

### 0.10.0: all Unown forms and Cape Brink

For Unown, **Configure → Pokemon → Unown form** selects Any, A–Z, ! or ?. Every generated form must match its PID, imported Tanoby chamber, encounter slot, level and rejection history. Missing or mismatched chamber metadata fails closed. The small chamber/form rules are factual constraints; encounter tables, names and artwork still come from your ROM cache. Form selection survives saved builds and clears when switching to another species.

Previews now select Unown artwork from the actual result PID, with matching form names. The form picker also previews the highlighted letter. All 28 forms have been exported from both FRLG hosts and independently checked.

Frenzy Plant, Blast Burn and Hydro Cannon are available for their compatible fully evolved Kanto starters using the host's Cape Brink rules. These results have friendship/happiness 255 and explicit tutor provenance. No tutor-use flags are consumed. Remaining egg-move and pre-evolution history gaps, other games' tutors and broader unfinished work are listed in [COVERAGE.md](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/legalmon/COVERAGE.md).

### 0.9.0: more wild spreads and standard tutor moves

Imported ordinary FRLG wild slots now have Method H1, H2 and H4 profiles. H2 skips a RNG call before the IV words; H4 skips one between them. Validation, exact-IV anchor searches, perfect finders and proof replay use the selected method. Static/gift encounters and Unown do not receive these ordinary-wild variants. Nature/slot/level proofs remain bounded; this is not a complete retail timing simulator.

The move picker includes the 15 standard FRLG tutors using `pokemon/tutor.lua` from your imported ROM cache. Tutor-only requests show their source in the legality report and are rechecked at delivery. No move tables are bundled. Older caches without a supported tutor table simply do not offer these moves; re-import with the current host to obtain the table. Cape Brink was added in 0.10.0 and supported pre-evolution histories in 0.12.0; compatible direct-father egg moves were added in 0.13.0. Generation does not consume one-use tutor flags or prove that your save visited a tutor.

### 0.8.0: alternate acquisitions and explicit breeding

Validate now searches all eligible implemented acquisition profiles instead of choosing only the first family. Paths receive bounded round-robin work, so a difficult or impossible early path does not starve later origins. Resume preserves every child cursor. L/R browsing and the shiny/perfect finders consider alternate profiles, deduplicating identical PID/IV/ability/OT/language outcomes. The progress bar measures a combined work budget, not global completeness.

Choose **Configure → Pokemon → Acquisition → egg** for an explicit FRLG breeding route, including species already obtainable as starters, gifts or wild encounters. Minimum levels include the egg/evolution path. Marill and Wobbuffet also have non-incense level-5 routes. Direct-father egg moves are now supported; recursive parent ancestry remains outside scope.

Before injection, the selected profile is reconstructed from the trusted current ROM catalog and checked against the unchanged request. An unsupported profile prevents an exhaustive negative conclusion; an impossible early profile no longer rejects a later valid route. See [the coverage audit](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/legalmon/COVERAGE.md) for remaining work.

### 0.7.1: search completeness work

Poké Spot validation now runs its PID stage incrementally: pause and resume retain its cursor instead of failing after a synchronous million-seed scan. Shiny requests enumerate the complete 524,288-PID shiny domain for the selected trainer, using exact GameCube PID reversal and activation checks. The ordinary PID stage can resume across the entire 32-bit RNG period. The screen identifies PID versus IV/level stages, and reports include PID trial counts.

This does **not** make all Gen III spreads covered. IV searches still use one proven Poké Spot PID; exhausting its IV anchors now reports incomplete instead of implying global impossibility. See [the coverage audit](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/legalmon/COVERAGE.md) for the remaining encounter, move, breeding, GameCube and cross-profile gaps. Search checkpoints are in-memory, not saved across application restarts.

## Install and use

1. Use a current gen1recomp build with mod API 2 and FireRed/LeafGreen support. The integration was developed against commit `fab224458f9d5af79a82b5ff5338347ef74c0189`.
2. Import your own supported clean US FireRed or LeafGreen ROM through the game's normal importer. Both editions and their normalized 1.1 revisions are supported. Existing compatible Pokémon caches work; re-import if the screen reports an outdated or missing data format.
3. Extract the release ZIP into `mods/legalmon` in the game's mod directory, so `mods/legalmon/manifest.json` exists. Alternatively copy this whole folder there. Enable **LegalMon** in the mod manager, accept its declared `engine_internals` access, and restart the game session as prompted.
4. Open START in the ordinary overworld and select **LEGALMON**. It appears before SAVE. It does not appear in link rooms, Union Room or Safari menus, or when the mod is disabled.
5. Set Pokémon, IVs and moves, select **Validate**, review **Preview & send**, choose party or PC, and confirm generation. Save normally to retain generated Pokémon and saved builds. Keep a backup of your save when trying a new mod.

The repository gallery location `mods/examples/legalmon` is intentionally not discovered automatically. Move/copy it into the one-level mod directory to enable it. No engine source patch is required.

## Controls and quality of life

### Main menu

The home screen has six entries, all visible without scrolling:

| Entry | Contents |
| --- | --- |
| Configure Pokemon | Pokemon, IV constraints, moves, Hidden Power, locks/reroll and destination |
| Validate / Resume search | Check the current request or continue a paused/exhausted search |
| Preview & send | Inspect, compare, pin and confirm delivery |
| Finders & tools | All-31 finder, shiny seed finder, presets/builds, pins and legality/report |
| Results & style | Shiny-only filter, cries and sprite bounce |
| Close | Remember configuration and return to the game |

L is now a back button in menus. In previews and comparisons, L/R retain their previous/next-result meaning; B goes back. At the first result, L stays on that result and explains the boundary. Default keyboard shoulders are Q/E (also left/right Ctrl), not the letter L. The engine's Help/L=A shoulder interception is suppressed only while LegalMon owns input, without changing your saved control settings.

### All 386 species: implemented acquisition paths

The species picker lists all 386 Gen III species in National Dex order, using names and sprites from your ROM. Hoenn National Dex numbers are mapped to the correct internal FRLG species IDs. **All 386 have generated successfully on both FireRed and LeafGreen in the real-cache tests**, including cartridge serialization and independent PKHeX checks. `[!]` remains a fail-closed indicator for unavailable paths if your cache is incomplete or incompatible.

Coverage means at least one implemented legitimate acquisition route per species, not every distribution or trade chain. Original static/wild paths are preferred; breeding fills remaining breedable species. Event-only species use the specific distributions below. Exact requests outside these implemented paths still fail rather than fabricating an acquisition. For example, Aura Mew and 10 ANIV Celebi cannot be shiny, and FRLG roaming beasts cannot have all-31 IVs. Other legal origins for the same species may exist outside this release's scope.

Under **Configure Pokemon → Pokemon → Origin**, choose Any supported or an exact source game: FireRed, LeafGreen, Ruby, Sapphire, Emerald, Colosseum or XD. Exact origins are preserved through validation and both finders. Unsupported species/origin pairs fail rather than silently changing games. The preview/report shows the actual selected acquisition. Source games model a legitimate transfer into FRLG, not a requirement to run another game or import its ROM.

### Colosseum / XD and original trainers (0.7.0)

GameCube coverage now includes **all 48 regular Colosseum Shadows, all 83 XD Shadows, all nine XD Poke Spot species, and all three Japanese e-Reader Shadows**, plus starters, the listed gifts/trades and supported evolutions. This does not promise every rematch configuration or every exact spread. Existing Any-supported routes retain priority. Choose the exact origin to request a GameCube route.

- **Shadow teams:** forward-simulates NPC IDs, preceding party members, fixed nature/gender, independent ability calls, preceding Shadows and PID rejection loops. XD checks shininess against both CPU and player IDs. Colosseum's preceding non-Shadows are protected against CPU shininess. The selected encounter configuration is replayed from a stored team seed; this replaces the first-roll-only restriction. Searches use a full-period ordering of team-start seeds to avoid clustered duplicate outputs and run in small UI batches.
- **Poke Spots:** Rock (Sandshrew/Gligar/Trapinch), Oasis (Hoppip/Phanpy/Surskit), Cave (Zubat/Aron/Wooper). Activation/slot/PID and collection-animation/level/IV stages have separate recorded seeds. Both are verified before delivery. Randomized met level, independent ability and evolutionary level floors are enforced. Shiny and all-31 requests are supported where the actual proofs match.
- **Japanese e-Reader:** Togepi, Mareep and Scizor, plus supported evolutions. All IVs are zero; nature/gender and the full NPC team are replayed. The result has Japanese language, the National Ribbon and the explicit Latin nickname `MON`, avoiding bundled Japanese species-name assets. Use a male original trainer with 1–5 uppercase Latin letters/digits; longer or unsupported names are refused, not truncated. The preview and confirmation disclose language/nickname. Shiny generation is supported with a matching proof. Nonzero IV requests fail strictly.
- **Exact route picker:** Configure → Pokemon → Acquisition selects `shadow`, `starter`, `trade`, `gift` (Mt. Battle), `pokespot`, `ereader`, `egg`, `cartridge` or Any. It is preserved by saved builds and finders. `cartridge` excludes the separately selectable egg route. Use this to request e-Reader Togetic/Ampharos or evolved NPC trades rather than another acquisition of the same species. Selecting a species uses the minimum level for the selected origin and route. Unsupported combinations never fall back silently.
- **Starters:** Colosseum Espeon/Umbreon and XD Eevee (including its supported evolutions). Seeds are derived from the exact OT IDs and startup order. Espeon's proof includes the preceding Umbreon generation; Colosseum starters are male and nonshiny. XD Eevee can be shiny if its actual correlated seed allows it. Arbitrary perfect IVs are not guaranteed for chosen IDs. L/R browses the finite supported starter seeds; exhausted name-screen coverage is reported as incomplete.
- **NPC gifts/trades:** Colosseum DUKING Plusle (fixed TID 37149/SID 0, nonshiny); XD HORDEL Elekid and DUKING Meditite/Shuckle/Larvitar, plus supported evolutions. XD uses the NPC's fixed name/TID and the receiving player's SID. Elekid retains its required ZAPRONG nickname through evolution. These are not purified Shadows and do not get a National Ribbon. Custom OT overrides are refused rather than silently discarded; select Use your trainer to retain the required NPC identity.
- Uses the GameCube RNG's IV → independent ability → high/low PID sequence, not cartridge Method 1. XD Shadows reject shiny requests and replay PID rerolls; Colosseum Shadows and XD Mt. Battle gifts can be shiny. Purified Shadows carry the National Ribbon. XD origins carry their required fateful flag. Cartridge exports encode the shared CXD game value; the mod's report retains which source game was modeled.
- **Scope limits:** additional bonus-disc distributions, every alternate rematch/already-seen-Shadow configuration, and purification-only/exclusive moves are not offered. Choose supported FRLG moves learned after transfer. No Shadow moves or unpurified Pokemon are injected. This is acquisition coverage, not proof of a historical capture or exhaustive coverage of all possible builds.
- **Configure → Original trainer:** use your trainer, edit a custom name/TID/SID/gender, or randomize a draft and review it before applying. IDs are 0–65535; supported English names are 1–7 characters. Randomization uses a local deterministic sequence, never advances gameplay RNG, and defaults to a male OT. Your player identity is never changed.
- GameCube OTs must be male and need a trainer-ID RNG proof. Naming-screen traversal now handles ball-spawn branches as well as no-spawn fadeout frames, with a 4,096-node safety budget. Ruby/Sapphire OTs also require correlated IDs. Unproven exact IDs are never silently repaired: randomize the draft or choose another origin. Fixed-event/NPC OTs cannot be overridden.
- Changing OT clears validation; shininess, both finders, reroll locks, previews and delivery use the selected OT. Other-OT Pokemon can be subject to the game's traded-Pokemon behavior, including obedience rules.

Search limits are explicit: normal searches examine a million candidates per budget and can resume; NPC-team IV searches are not exhaustive on budget expiry. Poke Spot PID selection has a separate million-seed budget; its IV search then preserves that valid PID. The broad all-31 finder samples 128 NPC team starts, so no result is not an impossibility claim. A current-seed Poke Spot finder tests that same numeric snapshot at both stages; broader validation may use separate stage seeds. Neither changes gameplay RNG.

Validation includes both FRLG caches, all 386 species, GameCube minimum levels, custom/NPC OTs, starter correlations, team replay, abilities, e-Reader language/evolutions/shininess, naming ball-spawn branches, Poke Spot shiny/perfect results, alternate acquisition searches, explicit egg routes, H2/H4 wild variants, all 28 Unown forms, FRLG tutors, imported NPC trades/evolutions and proven pre-evolution level-up/TM/tutor histories, direct-parent inheritance and bounded parent-chain/Sketch combinations. **19,203 exported encrypted cartridge records passed the pinned independent PKHeX checker.** This is regression evidence, not a claim that every possible request has been exhaustively verified.

### Controls

- Native 240×160 layout, ROM font, the player's selected window frame, and ROM front sprites. The selected species is shown while browsing; shiny requests and validated shiny results use the shiny palette. No sprite files are shipped in the mod.
- D-pad moves the cursor; A chooses; B/L go back in menus. Left/right jumps five rows. The species picker header shows the selected Pokémon's National Dex number, unchanged by filtering; Search/Clear controls are not numbered. Other lists show a position counter.
- Species and move pickers have **Search / filter**. Type a name, Backspace to delete, Enter to accept or Escape to cancel. Game hotkeys are intercepted only while the text editor is active. Controllers can use the on-screen alphabet, SP, DEL and OK with D-pad/A.
- Available abilities, genders, acquisition/evolution level floors and move sources are shown while configuring. Selecting a Pokémon from the species picker/search automatically sets its lowest supported acquisition/evolution level for the selected origin (or any supported origin). This can raise or lower the previous level; other constraints stay unchanged and validation is cleared. You can then adjust Level manually. Unsupported species/origin pairs retain the old level and fail validation rather than inventing a legal floor. This is the acquisition floor, not a promise that retained move/IV/nature constraints are feasible at that level.
- **Any legal**, **Physical attacker** and **Special attacker** presets keep species and level, and explicitly reset other choices. Attacker presets request Adamant/Modest and offensive/Speed IV ranges of 25–31. Every preset still requires validation.
- Each IV supports Any, an exact integer, or a min/max range. Bulk shortcuts offer all Any, all minimum 20, all minimum 25, or all exact 31. Minimum 20 means all six IVs are in 20–31. A confirmation describes the replacement. Exact 31 in every stat is not guaranteed to exist with your other constraints.
- Search shows examined frames and the current search budget. A pauses/resumes; B pauses first and then returns; SELECT cancels and discards the search. **Resume search** continues at the same position. Editing a constraint invalidates the old result. Closing the screen discards its search; searches are not persisted across sessions.
- Failed validation preserves all choices. **Legality & report → Find alternatives** offers explicit changes for review. These are candidate requests, not claims of proven or mathematically nearest solutions; they require a new search. No automatic relaxation occurs.
- The read-only preview lists exact stats, moves, gender, ability, shininess, origin, met level/location and ball. The final confirmation defaults to Back. Party/PC capacity is shown; party overflow never silently redirects into a box. PC placement uses the game's first-free-slot routine.
- In the validated preview, **L/R browse matching Pokémon** without changing your species or constraints. L returns to a cached result; R advances to a cached result or searches for another valid PID/IV combination. The header and footer show your result number and controls. B stops a next-result search while keeping the current preview; R continues it. A search-budget limit is not proof that no further matches exist. Generation and reports use the selected result; editing constraints clears the results.
- Save up to 20 named favourites/custom builds. The last 10 successfully generated builds appear in Recent builds. These are detached request copies, not reusable validation approvals, and are saved with the normal game SAVE.
- **Export full report** saves plain text and prints the full report to the engine log for copying. Desktop clipboard access is intentionally not requested: the engine sandboxes it. The file is `mod_storage/<edition>/<playthrough-id>/legalmon/reports/latest.bin` beneath the game's save directory. Despite the `.bin` extension required by the byte-storage API, it is readable text; each export replaces the previous report. It includes the full request, seed, PID, IVs, IDs, acquisition and move sources. Export errors are shown rather than reported as success.

## All 31 finder

In a validated preview or IV/stat comparison, press **SELECT** to jump to the highest total IVs among results already found for that request. The preview shows the sum out of 186; ties select the first result. An active next-result search pauses with its position preserved. This does not search unseen seeds or prove a global maximum; use R to find more candidates, then SELECT again. Existing constraints, result order and consumed-proof safeguards stay unchanged. SELECT during initial validation still cancels that search.

Open **Finders & tools → All 31 finder** from LegalMon:

- **Check current game seed** reads a snapshot of the engine's live main RNG state without advancing it and interprets it with each species' acquisition method. Method 1/H1 results require their PID/IV and encounter proof. Eggs use the snapshot as their collection seed with displayed hypothetical-parent constraints. Restricted events require a seed within their actual 16-bit distribution domain. A failed check leaves your configuration untouched.
- **Any perfect Pokemon** checks all six Method 1 all-31 spreads (Modest, Calm, Docile or Timid), the corresponding supported wild proofs, and complete restricted-event seed domains. For eggs it offers up to eight perfect samples found in a bounded one-million-frame search, **not all possible perfect eggs**. Choose a species for numbered spreads with nature, gender and shiny (`*`) badges; ability and seed appear in the footer. The non-egg nature limitation must not be applied to eggs.
- **Keep my choices** changes only IV constraints to six exact 31s. Finite Method 1/H1/event domains are exhaustively checked where applicable; egg searches are bounded and resumable. Incompatible exact nature, gender, ability, shiny or move requests are never silently relaxed.

Broad finder results require confirmation before replacing species/IVs, clearing extra IV filters, allowing any nature/gender/ability, selecting automatic moves, and raising your current level only to the species' acquisition/evolution floor when necessary. Shiny-only remains enforced when enabled; otherwise shininess is unrestricted. The review shows the actual result and seed. L/R in the preview browses the perfect spreads for the chosen species. Normal party/PC safeguards and report export still apply.

These are synthetic acquisition proofs, not an RNG-manipulation timing guide. The mod neither reseeds nor advances live game RNG, and it does not promise the next natural encounter will use a displayed seed. Normal gameplay may change the live seed after the snapshot. Event shininess uses the fixed event OT's IDs. Egg proofs assume the displayed compatible parents/IVs; they do not inspect or consume actual daycare parents.

## QoL and shiny tools (0.2.0)

- **Results & style → Shiny-only results** filters normal validation, L/R searches and perfect finders. An exact `Shiny: No` request reports a conflict rather than being silently changed. Toggling clears existing validation. If no all-31 spread is shiny for your trainer IDs, the perfect finder reports no match; it never changes IDs or fabricates a PID.
- **Shiny seed finder → Check current shiny seed** takes one live main-RNG snapshot and lists matching proofs using each species' implemented acquisition algorithm. Method 1, Unown, egg and event algorithms can yield different PIDs from the same numeric seed; fixed-OT event shininess uses event IDs, not yours. Eggs include hypothetical parental IVs. Shiny-locked events are excluded. This does not look ahead or advance RNG. Use normal validation with `Shiny: Yes` or shiny-only enabled to search other seeds. Its explicit review clears other constraints as described above.
- **Preview → Compare IVs & stats** shows old/new IVs and actual stats, signed differences, and highlighted changes. L/R browses while keeping the comparison visible. The baseline is the pinned result, otherwise the previous result (initially itself). Names, levels and natures identify both sides; higher is highlighted, not asserted to be competitively better.
- **Pin this result / Pinned results** bookmarks up to eight candidates during this open LegalMon session. Compare, restore a pinned preview after confirmation, remove individual pins or clear all. Restored pins retain consumed status, so an already delivered proof cannot be delivered again. Pins and search proofs are not persisted across close/reopen.
- **Locks & reroll** locks any of nature, gender, ability, shiny status or the six IVs. **Search unlocked** requires confirmation: locked fields use the selected preview's exact values, or existing constraints before validation; unlocked traits/IVs become Any. Species, level, moves, Hidden Power and aggregate IV filters stay. Locks only govern this action, not manual edits, presets or the broad finders.
- **Legality & report → Why no match?** explains validator errors and the known all-31 nature, shiny and Hidden Power conflicts. Alternatives are explicit proposals, not promised matches; budget exhaustion is never called proof of impossibility.
- **IV constraints** adds 0 Attack, 0 Speed, at least five perfect IVs (any five), and minimum IV total (0–186). Bulk shortcuts reset individual IVs and previous total/count filters after confirmation, while keeping Hidden Power constraints. High constraints may require continuing a bounded search.
- **Hidden Power** selects type and minimum strength (30–70), derived from Gen III IV bits. This filters IVs; it does not automatically teach the move. The preview and exported report show actual type/power. Formula cross-checked against the native engine and [pret's FRLG battle implementation](https://github.com/pret/pokefirered/blob/master/src/battle_script_commands.c).
- **Destination → Box 1–14** previews empty slots and asks for confirmation. Delivery uses the chosen box's first currently empty slot through the native storage routine. A full selected box fails without spillover or overwrite. The ordinary PC option retains automatic first-free placement. The currently selected PC box is preserved.
- **Remember your place:** closing stores configuration, picker filters/cursors, root cursor and style options in normal mod-save data; use the game's regular SAVE for persistence across game launches. Reopening requires new validation and does not automatically generate anything. Invalid stored UI data is sanitized.
- **Results & style** toggles ROM selection cries and an optional gentle sprite bounce (not new sprite frames). Native frames/fonts, shiny palettes and shoulder-button hints remain. The home header indicates READY, VALID, WAIT, PAUSE, FAIL or MORE (budget exhausted). No new image/audio assets are bundled.

## Legality scope

Supported acquisition paths:

- Either FRLG edition's non-event starters, fossils, gifts (excluding the Togepi egg), Game Corner prizes, stationary Pokémon and stationary legendaries. Edition-specific prize levels survive transfer.
- The active FRLG ROM's land, surf, Rock Smash and Old/Good/Super Rod tables using Method H1/H2/H4. Safari encounters use Safari Balls; other supported paths use Poké Balls. Tables and map sections are read from the user's imported cache, never shipped. The other FRLG edition's wild tables are not inferred from the active ROM.
- Selected RSE non-event static/gift paths: Hoenn starters and fossils, Castform, Beldum, Kecleon, Voltorb/Electrode, the Regis, Rayquaza, and edition-appropriate Groudon/Kyogre. Emerald also supports its Johto starter gifts and Sudowoodo.
- ROM-derived level, stone, ordinary trade, trade-item and friendship evolution paths, including supported transfers for evolutions unavailable directly in FRLG. A level-up evolution always requires a level above the actual rolled encounter level, even if that encounter is already above the usual evolution threshold.
- FRLG eggs for eligible breedable species, including those with existing wild/gift/static routes, hatched at level 5 in Pallet Town with stored met level 0. Parent compatibility, pending PID low half, collection PID high half, random IVs, three distinct inherited stats and parent choices are replayed. Reports list the hypothetical compatible parent species, Ditto, inherited IVs and any Sea/Lax Incense requirement. Parent PID/IV ancestry is not recursively reconstructed; these are legitimate-breeding assumptions, not evidence that your save owns those parents. Gen III baby species and the Nidoran/Volbeat/Illumise pending-PID species bit are respected.
- Wurmple's PID-dependent branch, Tyrogue's actual zero-EV Attack/Defense comparison, Ninjask/Shedinja evolution and Milotic beauty metadata. Milotic carries beauty and sheen consistent with prior Pokéblock feeding. These do not consume your items or mutate story progress.
- FRLG roaming Raikou/Entei/Suicune with the retail IV truncation: Attack 0–7; Defense, Speed and both Special IVs zero. Emerald roaming Latias/Latios retain full Method 1 IVs.
- All 28 Unown forms from their Tanoby chambers using high-first PID generation, form-specific rejection, encounter slot and met-level proof. Exact form requests never silently substitute another letter. This does not claim every possible RNG variant for Unown.

### Event origins

All-386 coverage requires going beyond the original non-event scope. Event results are visibly marked **EVENT origin**; fixed event trainers appear in the preview and final confirmation.

| Species | Implemented origin | Restrictions |
| --- | --- | --- |
| Mew | English Aura distribution, Ruby origin, level 10 | OT `Aura`, TID 20078, SID 0, shiny-locked, fateful |
| Celebi | English 10 ANIV distribution, Ruby origin, level 70 | OT `10 ANIV`, TID 10, SID 0, shiny-locked |
| Jirachi | English WISHMKR, Ruby origin, level 5 | OT `WISHMKR`, TID 20043, SID 0; legitimate shiny seeds permitted |
| Lugia / Ho-Oh | FRLG Navel Rock, level 70 | Historical event-ticket acquisition, fateful |
| Deoxys | FRLG Birth Island, level 30 | Historical event-ticket acquisition, fateful; host-specific form |

The three fixed-OT distributions use their restricted 65,536-seed domains, high-first PID generation and event-specific anti-shiny/OT-gender rules. User trainer IDs are never substituted to make an event shiny. Current moves remain restricted to the final species' FRLG level-up/reminder, TM/HM and imported standard tutor moves; exclusive event moves are not added automatically. A generated record is not evidence of attendance at a historical distribution.

All generated Pokémon have zero EVs; Rare Candies provide a legitimate training path. The current level may exceed the original met level. Normal cross-origin results retain source-game met location/level and the requested trainer's identity; fixed-OT gifts retain their original event trainer instead.

Altering Cave, RSE NPC trades, other event distributions, RSE wild encounters and GameCube methods outside the subset above remain unimplemented. A refusal is relative to this supported scope, not a statement that the build is impossible across every Gen III origin. Breeding routes are exposed separately, but parent histories and other games' breeding algorithms are not exhaustively modeled.

Moves support the final species' FRLG level-up/move-reminder moves at the requested current level, ROM TM/HM compatibility, imported standard tutors, Cape Brink species rules and acquisition-bound pre-evolution level-up/reminder, TM/HM and tutor histories plus compatible parent-chain egg moves and witnessed parental Sketch. Move histories involving special evolution methods, unmodeled Sketch setups and special-evolution parental histories, other games' tutors and cross-game-exclusive moves remain unimplemented. Illegal, duplicate or malformed exact move requests fail. English Pokémon names come from the ROM; this MVP requires a 1–7 character supported English trainer name.

Method 1 is implemented independently using the Gen III LCG (`0x41C64E6D`, increment `0x6073`) with exact 32-bit arithmetic under LuaJIT. It emits PID low, PID high, IV word 1 and IV word 2 in order. Nature, gender, ability, shiny XOR and IV constraints must all match. The result is replayed from its seed before construction and rechecked against the current request/trainer before delivery. Single-ability species store ability slot zero.

Methods H1/H2/H4 additionally reverse the nature-selection loop, prove that all earlier PID pairs were rejected, and reconstruct encounter slot and met-level rolls. They apply the evolution floor to the rolled met level, not just the table minimum. Land/surf proofs allow Sweet Scent; fishing allows waiting for a bite. Rock Smash uses a conservative PKHeX-compatible activation check with the White Flute rate modifier; FRLG's separate encounter RNG is not simulated. This intentionally restricts results rather than promising exhaustive retail encounter timing. Each reverse proof is capped at 4,096 boundaries; reaching that cap is **incomplete**, never proof of impossibility.

For regular Method 1/H1/H2/H4 and Unown, exact HP, Attack and Defense IVs permit examining every RNG state compatible with that first IV word (131,072 states per method); no matching frame means **impossible within implemented paths** only when no proof hit its reversal cap. Restricted-event searches check all 65,536 distribution seeds. Neither finite child domain can be extended or wrapped with Resume or R; the scheduler continues other paths. Eggs and roaming-IV searches use a one-million-frame budget and report **search exhausted, impossibility not proven**. A result never changes exact requirements. Search runs in small batches without consuming the gameplay RNG.

Names, stats, abilities, learnsets, TM/HM compatibility, evolution data, PP, sprites and fonts are loaded from the player's ROM cache, not bundled. The small acquisition rules are independently expressed factual constraints, not ROM bytes or a copied PKHeX encounter database. Cache identity must match a recognized edition and Pokémon extraction format. Species-stat/meta/ability or move-PP conflicts with other mods block construction. Arbitrarily modified/tampered caches are outside the trust model; a cache's provenance marker is not a cryptographic rehash of every extracted file.

Generation is a synthetic edit with legitimate constraints; it is not proof of an actual capture and does not consume story gifts or set their event flags. It does not enforce one-per-save gift history. The internal check is deliberately narrower than all of PKHeX's checks; do not treat it as a promise of universal PKHeX acceptance. For version 0.17.0, **19,203 exported encrypted records passed the pinned PKHeX.Core legality analyzer and checksum checks**, including all 386 species on each host at ordinary and advertised minimum levels, supported source-game alternatives, explicit breeding routes, H2/H4 wild profiles, all 28 Unown forms, compatible FRLG tutor moves, pre-evolution-exclusive moves including evolution-level teaching, direct-parent egg moves and bounded parent-chain/Sketch samples, imported NPC trades and evolutions, extra egg/event/roamer samples, shiny WISHMKR, GameCube acquisitions and shiny/nonshiny Poké Spot results. These are regression samples, not exhaustive validation of every possible request. Full interactive in-game playtesting remains necessary.

## Source references

Behavior was checked against the current [PKHeX source](https://github.com/kwsch/PKHeX) at `17157eb18013dc29a44f7bb7810117390431087b`, particularly:

- `PKHeX.Core/Legality/Encounters/Templates/Gen3/EncounterStatic3.cs`
- `PKHeX.Core/Legality/Encounters/Data/Gen3/Encounters3FRLG.cs`
- `PKHeX.Core/Legality/Encounters/Data/Gen3/Encounters3RSE.cs`
- `PKHeX.Core/Legality/RNG/Algorithms/LCRNG.cs`
- `PKHeX.Core/Legality/RNG/ClassicEra/Gen3/MethodH.cs` (why wild encounters cannot use a bare Method 1 check)
- `PKHeX.Core/Legality/RNG/ClassicEra/Gen3/Daycare3.cs`
- `PKHeX.Core/Legality/Moves/Breeding/MoveBreed3.cs` and `Breeding.cs` (inheritance categories and split species).
- [FireRed daycare implementation](https://github.com/pret/pokefirered/blob/master/src/daycare.c) and the host's `src/core/game3/breeding.lua` (parent slots and shared level-up inheritance). Rules are independently expressed; reference code and ROM move tables are not bundled.
- [FireRed Sketch implementation](https://github.com/pret/pokefirered/blob/master/src/battle_script_commands.c) (permanent copying and excluded move checks). Special battle setups beyond the witnessed subset above are not assumed.
- `PKHeX.Core/Legality/Encounters/Data/Gen3/EncountersWC3.cs` and the common event RNG checker
- `PKHeX.Core/Legality/RNG/CXD/MethodCXD.cs`, GameCube encounter profiles and `TrainerIDVerifier.cs` (RNG ordering, trainer-ID constraints, purification and shiny restrictions)

Egg inheritance and Unown's reversed PID word order were also checked against [pret's daycare reconstruction](https://github.com/pret/pokefirered/blob/master/src/daycare.c) and [wild encounter implementation](https://github.com/pret/pokefirered/blob/master/src/wild_encounter.c). Tests independently replay the wild proof and compare egg inheritance with the host's native breeding implementation.

PKHeX is GPLv3. No PKHeX source or resource files are copied or shipped. gen1recomp's existing license and attribution terms apply to the host project; see its root `LICENSE.MD`. The mod declares `engine_internals` because FRLG's native modal stack, ROM Pokémon pack and PC-delivery routines are not fully represented in the generation-neutral public UI API. It uses the existing start-menu/input hooks without replacing retail menus or introducing a new engine API.

## Development and tests

From the gen1recomp repository root, with LuaJIT on PATH:

```sh
python3 tools/modkit.py validate mods/examples/legalmon
python3 tools/modkit.py lint mods/examples/legalmon
luajit mods/examples/legalmon/tests/legalmon_test.lua
luajit mods/examples/legalmon/tests/screen_test.lua
luajit mods/examples/legalmon/tests/qol_test.lua
luajit mods/examples/legalmon/tests/origins_test.lua
luajit mods/examples/legalmon/tests/expanded_test.lua
luajit mods/examples/legalmon/tests/gamecube_test.lua
luajit mods/examples/legalmon/tests/profiles_test.lua
luajit mods/examples/legalmon/tests/wildvariants_test.lua
luajit mods/examples/legalmon/tests/unown_test.lua
luajit mods/examples/legalmon/tests/trades_test.lua
luajit mods/examples/legalmon/tests/movehistory_test.lua
luajit mods/examples/legalmon/tests/eggmoves_test.lua
luajit mods/examples/legalmon/tests/breedingchains_test.lua
python3 tools/modkit.py pack mods/examples/legalmon -o legalmon-0.17.0.zip
```

Set `MODKIT_LUAJIT` to a LuaJIT executable path if it is not on PATH. Tests use synthetic species data and cover RNG vectors/reversal, impossible exact spreads, malformed requests, search exhaustion, edition/evolution constraints, native hook integration, party/PC capacity, duplicate/stale proof refusal, encrypted cartridge record round trips, UI search/controllers, presets, confirmation, favourites and report export. Test fixtures are excluded from the distributable archive.

Map metadata is read with a narrow reader for the importer's canonical `id` and `regionMapSectionId` fields; unsupported encodings or duplicate fields are skipped. It is not a general-purpose JSON validator and relies on the clean imported-cache trust model. LegalMon does not request network access. A `LIMIT` home badge means a bounded encounter proof was incomplete.

Optional real-data test, reading your existing cache without editing it or your save:

```sh
LEGALMON_GAME=leafgreen LEGALMON_CACHE="/path/to/leafgreen/data/generated/gba" \
  luajit mods/examples/legalmon/tests/rom_test.lua
```

Repeat with `firered`. This exercises every supported species with actual ROM data, engine stat calculation, normal-save serialization, cartridge record encryption/checksum and shiny interpretation. It does not substitute for an independent PKHeX legality analysis of an exported save or for interactive playtesting.

### Optional independent PKHeX check

Requires .NET SDK 10 and a separate PKHeX source checkout. The tested reference is commit `17157eb18013dc29a44f7bb7810117390431087b`. Keep all build products and exported Pokémon outside the mod folder; none belong in a release ZIP.

```sh
exports="$(mktemp -d)"
checker="$(mktemp -d)"
cp mods/examples/legalmon/tests/pkhex/Check.csproj mods/examples/legalmon/tests/pkhex/Program.cs "$checker/"
LEGALMON_EXPORT_DIR="$exports" LEGALMON_GAME=leafgreen \
  LEGALMON_CACHE="/path/to/leafgreen/data/generated/gba" \
  luajit mods/examples/legalmon/tests/rom_test.lua
# Repeat the export command for firered into the same directory.
dotnet run --project "$checker/Check.csproj" \
  -p:PKHeXSource="/absolute/path/to/PKHeX" -- "$exports"
```

The test exports synthetic-trainer, encrypted 80-byte box records. The checker explicitly decrypts this known format before analysis, avoiding ambiguous encrypted/decrypted auto-detection; these are not ordinary decrypted `.pk3` interchange files despite the test filename extension. It exits unsuccessfully on any illegal record, invalid checksum or empty export directory. Source compilation is optional development tooling, not a runtime dependency. Do not publish the exports, ROM caches or third-party build products.


## Screenshot gallery

Native UI renders from development, using fixture/demo state. Some images predate later menu additions; see the feature documentation above for the current release.

### Compare

Historical preview (older build): [legalmon-compare](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-compare.png).

### Ereader Confirm

Historical preview (older build): [legalmon-ereader-confirm](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-ereader-confirm.png).

### Ereader

Historical preview (older build): [legalmon-ereader](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-ereader.png).

### Gamecube

Historical preview (older build): [legalmon-gamecube](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-gamecube.png).

### Home

Historical preview (older build): [legalmon-home](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-home.png).

### Perfect

Historical preview (older build): [legalmon-perfect](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-perfect.png).

### Preview

Historical preview (older build): [legalmon-preview](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-preview.png).

### Search

Historical preview (older build): [legalmon-search](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-search.png).

### Settings

Historical preview (older build): [legalmon-settings](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-settings.png).

### Species

Historical preview (older build): [legalmon-species](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-species.png).

### Spreads

Historical preview (older build): [legalmon-spreads](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-spreads.png).

### Style

Historical preview (older build): [legalmon-style](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-style.png).

### Trade

Historical preview (older build): [legalmon-trade](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-trade.png).

### Trainer

Historical preview (older build): [legalmon-trainer](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-trainer.png).

### Later release examples

Historical preview (older build): [Imported NPC trade](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-npc-trade.png).

Historical preview (older build): [Unown form picker](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/legalmon-unown-picker.png).
