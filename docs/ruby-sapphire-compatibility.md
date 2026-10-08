# Ruby/Sapphire feature parity audit

Implementation checked against engine 0.3.56 on Mac and 0.3.57 on Thor QoL Test. “Shared” means the implementation uses common engine APIs; it does not mean every gameplay interaction has been manually tested.

## Main packages

| Package | Ruby/Sapphire implementation and deliberate differences |
| --- | --- |
| LegalMon | Native wild, static and egg acquisition profiles, edition origin and RS PID/IV/inheritance rules. |
| Event Distributions | Compatible generated/exported distributions; native Eon Ticket with Ruby Latias / Sapphire Latios. No native Birth Island, Navel Rock or Faraway Island journeys in RS. |
| Shiny Hunter | Native RS shiny-odds generation and hunting paths; no second IV roll. Continuous hunting uses the shared controller. |
| Auto Breeder | Native Route 117 daycare and RS egg generation; no Emerald-only breeding bonuses. |
| Encounter Tour | 26 native destinations: static encounters, gifts, fossils, trades, ordinary Kecleon and Southern Island. |
| Encounter Reset | 28 reset entries plus three repeat starters, including prepared level-45 Groudon/Kyogre battles after the original encounter. Original story/starter choice retained; already-unlocked roamer only. |
| Gen3DualScreen | Native RS PokéNav, bag, summary, PC and progression data; common Home layout and mod integration. Move-selection touch supports sparse slots and Cancel. |
| QoL Suite | All 32 components accounted for below; game-specific functions remain scoped to games that have them. |

## All 32 Suite components

| Component | Parity / native difference |
| --- | --- |
| Capture Assistant | Shared capture calculations; uses the active game’s battle state. |
| Day Care Viewer | Route 117 in R/S/E; native RS pending PID/inheritance. Everstone, Flame Body/Magma Armor and Volt Tackle breeding bonuses remain Emerald-only. |
| Disable L/R Help | FR/LG only. Hoenn has no equivalent Help System to disable. |
| Fly Teleport | Native destinations per game; R/S has 16. Progression locks default on; optional Unlock All stays explicit. |
| Quick Field Actions | Native RS Cut, Rock Smash, Strength, Surf, Waterfall and Dive script paths; ownership and badge gates retained. |
| Sorted Bag | Shared bag list sorting; RS action-grid touch mapping is handled by Dual Screen. |
| Battle Ball Shortcut | Shared battle bag shortcut. |
| Battle Bar Speed | Shared HP/EXP animation options. |
| Held Berry Replacement | Shared held berry replacement. |
| Dex Companion | Active game’s encounter data and Pokédex records. |
| Faster Center Healing | Shared Center healing animation hook. |
| HM Field Kit | Owned HM plus native badge/location gates; a non-egg helper need not learn the move. Sweet Scent remains available through the existing field action. |
| Hoenn Tools | R/S/E only; detailed differences below. |
| Hold Fast Forward | Shared hold-to-speed control. |
| Fast / Instant Text | Shared text speed options. |
| Key Item Help | Edition-specific key items. RS omits Emerald island-ticket and Sudowoodo hints. |
| Town Map Companion | Native RS PokéNav map; services describe separate contest ranks and Battle Tower instead of Emerald’s tents/Frontier. |
| Party Held Items | Shared party item actions. |
| Party Nickname | Shared party rename action; rendered portrait/keyboard overlap still requires visual verification. |
| Party Move Reminder | RS native reminder and Heart Scale payment; FR/LG retains mushrooms. |
| Quicker Save Confirmation | Shared save confirmation shortcut. |
| Quiet EXP | Shared EXP message suppression. |
| Repel Reuse Prompt | Native R/S/E repel variable; normal item consumption. |
| Reusable TMs | Shared TM retention; HMs retain their normal ownership gates. |
| Running From Start | Native Hoenn running gate; FR/LG keeps its own flag. |
| Shop Owned Count | Shared normal-shop owned count. Decoration inventories are excluded rather than treated as bag items. |
| Expanded Summary Info | Native RS summary delegate and transition guards; battle/enemy editing remains blocked. |
| VS Seeker Readiness | Trainer’s Eyes in RS, Match Call in Emerald, battery readiness in FR/LG. |
| Scrollable Start Menu | Shared menu; no move/resize feature restored. |
| Pokemon Services | Native RS shops, Route 117 daycare, reminder and deleter scripts. |
| Quick Heal Party | Shared item-based healing; challenge restrictions apply. |
| Summary IVs | Native RS party/wild summary panel with selection/transition guards. |

## Eight Hoenn companions

| Companion | Ruby/Sapphire versus Emerald |
| --- | --- |
| Rematches | Trainer’s Eyes and native ordinary-trainer readiness; no Emerald Gym Leader Match Call path. |
| Berry garden | Native planting sites, nearby-tree grouping, growth information and safe adjacent teleports. |
| Battle facility | RS Tower streaks and native Level 50/100 trio eligibility; Emerald keeps its seven Frontier facilities. No BP or Symbols invented for RS. |
| Feebas | Active edition’s Route 119 tile geometry; exact native spot RNG arithmetic using a private seed. |
| Contest/Pokéblock planner | Active edition’s move data, condition, feeding preview and combos; RS contests are in four cities. |
| Bike switch | Immediate Mach/Acro swap, native riding restrictions and registered-item preservation. |
| Daily events | Shoal tides and Mirage Island in all Hoenn games; Terra/Marine weather caves only in Emerald. |
| Secret Base tools | Native locations, decoration inventory and registry management. |

## Intentional exclusions

RS Groudon/Kyogre now support prepared repeat battles in Cave of Origin B4F after the original encounter. Their original weather/NPC cutscenes are not replayed. Steven’s first Kecleon demonstration and Fortree’s fleeing roadblock remain excluded: resetting their encounter flags alone would not safely restore their story scripts. The ordinary Kecleon battles are included. English Emerald native Old Sea Map/Mew unlock remains excluded. Emerald-only Johto starter rewards, Frontier, weather caves and breeding bonuses remain Emerald-only.

## Evidence and remaining verification

- All eight clean production staging trees pass engine modkit `validate --strict` and `lint`.
- Five-game automated Suite integration: 314 assertions per game; collection startup: 42 checks per game.
- Native RS fixtures cover Eon Ticket receipt/serialization, resets, HM scripts and gates, bag action-grid ordering, summary selection, services, route objectives and Hoenn tools.
- Tower parity checks exercise native level/species/item/slot rules and the actual menu actions, with save contents unchanged by previews.
- Previous generated specimen checks: 3,962 event exports and 134 shiny/LegalMon exports passed PKHeX. This verifies those specimens, not all possible future output.
- Still required before declaring release-ready: rendered menu/touch review, broader save/reload gameplay, Mac/Thor play sessions and fresh RS screenshots. Existing screenshots do not demonstrate RS compatibility.

Download the current packages from the [latest collection release](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/latest).

Mascot repeat tests cover original-story gating, saved preparation, wrong location, no conscious party member, busy state, rejected battle start, one-shot consumption and the real native battle bridge generating level-45 Groudon/Kyogre. Native battle start/end preserve the existing story flags and variables. Hardware battle rendering/capture still needs gameplay verification.

## Additional local verification

Ruby and Sapphire now pass file-based save/reload tests for Auto Breeder eggs, Event Distributions Pokémon/receipts and duplicate blocking, native daycare deposits/withdrawals/fees, and one-use prepared starters. A breeder job retained from the previous session cannot deliver into the reloaded session. These tests use isolated files and the engine serializer/native actions; the normal in-game Save menu still needs gameplay verification.

Desktop layout policy tests pass for macOS, Windows and Linux (side by side and separate window), plus Android’s separate-screen behaviour. Home layout tests pass for migration, 24 compact launchers, mixed widget sizes, moves, swaps, reflow and bounds. These are layout/control-model tests, not hardware rendering checks.

Screenshot status: experimental trace captures show incorrect native RS small-text rendering. The separate native preview runner exits with code 137 on this Mac. Those captures are not approved for documentation and have not replaced any screenshots. Native rendering must be checked before deciding whether the issue is in the preview path, imported assets or game renderer.

### Day Care nature display correction

Ruby/Sapphire Day Care previews now read the native `gNatureNames` table. The previous FR/LG table lookup could crash the refreshed screen after a successful deposit. Native-cache regression checks cover deposit, read-only preview and withdrawal for all 25 natures in both Ruby and Sapphire.
