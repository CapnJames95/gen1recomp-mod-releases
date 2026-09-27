# Quick functional pass — 27 September 2026

**Result: all 37 mods passed their selected automated functional checks.** 105 successful suite invocations after correcting the harness paths. Both FireRed and LeafGreen were covered. No mod implementation was changed by this pass.

These are headless behavior and native-engine integration tests with synthetic sessions and existing imported data, not an interactive device playthrough. Player saves were not opened or changed. External PKHeX, physical controllers, long-running gameplay and every story state were outside this quick pass.

## Findings

- No functional regression found in the selected tests.
- All 37 mods loaded together in both editions; companion integration passed 306 assertions per edition.
- All 25 independent QoL behavior suites passed in both editions (50 runs); combined loader/reload/teardown and imported-data checks also passed.
- Scrollable Start Menu source was edited by another workflow during this pass. Its main.lua and tests/runtime.lua differed from the 0.1.1 ZIP at audit time. Both source and extracted release runtime tests passed; this is a snapshot, not certification of subsequent edits.
- All 37 ZIP CRC checks and published SHA-256 checks passed. 228 archived Lua/JSON/card files matched source; the two Scrollable Start Menu differences are recorded in package-check.json.
- The full repository publication audit stopped on an existing root .DS_Store. This is repository hygiene, not a mod-function failure. No existing metadata or user changes were removed.

## Per-mod checks

Every row passed; scope describes the selected smoke/regression coverage, not exhaustive gameplay certification.

| Mod | Checked functions |
| --- | --- |
| Auto Breeder | Native egg generation, filtering, inheritance, delivery and UI/loader controls |
| Capture Assistant | Native catch calculations, ball selection, risk/control checks and production loader |
| Day Care Viewer | Daycare inspection/actions, breeding data and native travel |
| Encounter Reset | Individual resets, map/state guards, confirmation/cancel and native Zapdos re-encounter |
| Encounter Tour | Tour controller, native static interaction and pause before travel |
| Event Distributions | 375 preview paths; filters, egg modes, ticket flags, battle/capture, persistence and duplicate guards |
| FRLG Dual Screen | All 37 mods load together; Home shortcuts, live editors, QoL toggles, input/pointers, native screens and encounter routes |
| FRLG Scrollable Start Menu | Fit/overflow, callbacks, wrap, confirmation, Safari, load order, disable/teardown and draw-error restoration; source and ZIP tests |
| LegalMon | Solver, delivery, persistence, UI, eggs/events/roamers and all 386 species using imported data |
| Pokemon Services | Remote services, native scripts, menu ownership and Dual Screen launch |
| Quick Heal Party | Medicine planning/application, inventory costs, guards and production loader |
| Shiny Hunter | Controller, encounter generation/reset, capture guards, pause, routes and native hooks |
| Auto Surf Prompt | Surf prompting and input guards |
| Sorted Bag | Pocket sorting and ordering |
| Battle Ball Shortcut | Ball popup/picker, confirmation, cancel and battle guards |
| Battle Bar Speed | HP/EXP animation speed and disabled behavior |
| Held Berry Replacement | Consumed-berry replacement and stock use |
| Dex Companion | Dex tools, caught status and evolution data |
| Faster Center Healing | Healing-presentation timing |
| HM Field Kit | Compatible field-move users without move injection |
| Hold Fast Forward | Hold speed, key/controller controls and restore |
| Fast / Instant Text | Text speed and disabled behavior |
| Four-Item Wheel | Registered-item selection/use/cancel |
| Key Item Help | Key-item guidance panels |
| Town Map Companion | Map service information |
| Party Held Items | Held-item actions and ownership |
| Party Nickname | Party naming and eligibility guards |
| Party Move Reminder | Move-reminder entry/payment paths |
| PC Box Tools | Box selection, batch move and cancel |
| Quicker Save Confirmation | Save-confirmation flow |
| Quiet EXP | EXP-message suppression with level-up/move-learning preservation |
| Repel Reuse Prompt | Repel reuse prompt and item handling |
| Reusable TMs | TM retention and native teaching |
| Running From Start | Running without shoes; disabled gate |
| Shop Owned Count | Owned-item count display |
| Expanded Summary Info | Nature and IV/EV panel |
| VS Seeker Readiness | Charge/readiness description |

## Reproduction and evidence

Engine checkout: `/tmp/frlg-dual-upstream`, commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. Interpreter: `/tmp/daycare-luajit/src/luajit`; Scrollable Start Menu runtime suite used `/opt/homebrew/bin/lua`. This is the available local engine, not a claim of testing every host release.

Commands and per-suite exit codes are in [final-summary.json](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest); logs and initial attempts are in [the results directory](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest). Environment supplied each edition’s `POKEPORT_VERSION`/`POKEPORT_GBA_CACHE`, mod-root variables, and `LUA_PATH=./?.lua;./?/init.lua;;`.

The initial QoL run used paths containing `..`, which the SDK filesystem could not load. Reruns used the engine-local `functional_collection` symlink pointing at this repository; all affected tests passed without changing their assertions or mod code. Initial scrollable draw runs were also superseded by runs using that verified path. Synthetic export/render artifacts were moved to `/tmp/mod-functional-pass-artifacts`, outside the repository.


## Follow-up legality check

Functional passes do not establish cartridge legality. The subsequent [generation legality pass](LEGALITY-PASS.md) found 18 rejected native engine-generated/exported samples; see that report for affected paths.

Those 18 failures are now fixed; the [post-fix report](LEGALITY-FIXES.md) records 438/438 passing Pokémon and complete-save validation.
