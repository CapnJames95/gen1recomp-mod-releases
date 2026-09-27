# Legality coverage audit

Version 0.17.0 is **not exhaustive Gen III legality coverage**. All 386 species have at least one implemented route; this is different from implementing every legal build, origin, move combination, or spread. External analyzer acceptance of regression samples is not a completeness proof.

## Search domains

| Domain | Implemented guarantee | Remaining gap |
| --- | --- | --- |
| Acquisition scheduler | Validation round-robins all eligible implemented profiles with independent cursors; delivery re-prepares the selected profile from the trusted catalog | Finite work budget and incomplete child domains still prevent universal coverage; source-game models below are missing |
| GameCube consecutive PID words | `gcPIDSeeds` reverses every possible low 16-bit state for a specified PID, without scanning or a heuristic cutoff | Reversal alone does not prove a preceding locked NPC team or trainer history |
| Poké Spot shiny PID stage | Enumerates all 524,288 shiny PIDs for fixed trainer IDs, reverses each eligible PID, and checks the modeled activation/slot rules | Does not enumerate all IV combinations for every PID |
| Poké Spot ordinary PID stage | Resumable full-period 32-bit RNG walk; finite domain is 4,294,967,296 states | Full traversal can be very slow; ordinary helper finders still use a bounded sample |
| Poké Spot IV stage | Independently proves IVs, ability, animation and met level for one selected PID | IV anchor exhaustion is incomplete, not global impossibility; R browses IV frames for this PID |
| Method 1 / H1 / H2 / H4 IV anchors | 131,072 states per method for an exact first IV word; H2 skips before IVs and H4 between IV words | Only imported FRLG ordinary wild profiles gain H2/H4; bounded nature rejection proofs and no exhaustive retail timing model |
| Unown | All 28 forms with imported chamber slots, form-specific PID rejection proofs and exact form constraints | Only implemented Unown H1 ordering; rejection traversal remains bounded |
| Restricted event distributions | All 65,536 distribution seeds for each implemented profile | Other distributions and their exclusive moves absent |
| FRLG NPC trades | All nine records from the active ROM, fixed PID/IV/ability/OT/nickname/contest data; one-record search domain; supported evolutions | No other-edition trade data inferred; a supported minimum offered-species level is used, not every possible trade met level; no proof of owning an offered Pokemon |
| GameCube locked teams | Replays selected NPC team configurations and target rejection rules | Alternate teams/rematches and seen-shadow variants not all modeled; perfect finder samples team starts |
| GameCube starter IDs | Enumerates candidate ID states and checks naming/startup paths | Name-screen proof traversal capped at 4,096 nodes |
| Eggs, roamers, unconstrained searches | Incremental sampled search, strict result replay | No completeness guarantee across parent histories or every seed |

Pause/resume keeps each current in-memory profile cursor. Closing/resetting the search or restarting the application is not a durable search checkpoint. Combined progress counts work units against a budget, not a percentage of all legal spreads. Each profile retains separate PID/IV counters. Identical PID/IV/ability/OT/language outcomes are deduplicated across paths; alternate provenance for an otherwise identical outcome is not separately listed. Finders check every eligible profile, but their candidate seed sets remain sampled where documented.

## Encounter and record coverage still needed

1. **Durable cross-profile searches:** the in-memory scheduler and trusted selected-profile delivery are implemented. Persistent checkpoints, domain-completion certificates and exhaustive child search methods remain necessary. A profile preparation failure is reported rather than silently treated as disproving other profiles.
2. **Cartridge acquisition models:** H2/H4 ordinary wild variants, all 28 Unown forms and active-edition NPC trades now use imported FRLG data. RSE wild tables and lead effects, RSE NPC trades and remaining encounter variants are still missing. Import game data from user-owned sources rather than bundling copyrighted tables/assets.
3. **Breeding:** explicit FRLG egg routes now coexist with wild/gift routes, including baby evolutions and non-incense Marill/Wobbuffet. Egg-list and shared-parent level-up moves require one compatible parent pair's final-species FRLG level-up/reminder, TM/HM or tutor sources. Shared moves must be known by both parents. Female-counterpart routes support Nidoran male and Volbeat; Ditto can occupy the mother slot only with a breedable male/genderless father from the offspring's own evolution family. Offspring split-bit and incense constraints remain enforced. Bounded move-chain proofs now resolve one complete moveset per parent, including ordinary pre-evolution level-up, TM/HM and tutor histories and witnessed parental Sketch. A circular chain without a source is rejected. The proof search has a 2,048-state/16-level cap, with unproven outcomes remaining incomplete. Special Sketch setups, missing witness sources, special parental evolution histories, other source-game inheritance/RNG variants and recursive parental PID/IV ancestry remain unimplemented.
4. **GameCube coverage:** alternate locked teams, rematches, prior shadow-state histories, and complete naming-screen reachability. Validate each profile independently, including rejected-PID chains, before admitting it.
5. **Moves:** the 15 standard FRLG tutors use imported compatibility data; Cape Brink uses host species rules and generates maximum friendship. Pre-evolution level-up/reminder, TM/HM and tutor moves now have acquisition-bound chronological proofs for ordinary level, friendship, stone and trade evolution chains. Special evolution chains, remaining egg-move histories, other games' tutors and exclusive gifts/events remain unmodeled. Individual move legality is not sufficient for mutually exclusive combinations.

Pre-evolution histories reserve one level gain per level-up evolution, while permitting level-up moves learned on that gain before evolving. The acquisition bound remains the preceding level, preventing a capture at the evolution level from skipping the required gain. TM/tutor teaching occurs before that gain. Stone/trade transitions can occur at the same level. A captured/already-evolved source cannot claim earlier teaching before acquisition. Missing special-history support produces an incomplete result, not proof that all legal histories are impossible. Parent move chains use these same chronological restrictions; parent PID/IV genealogy remains separate and hypothetical.
6. **Events and languages:** remaining distributions, region/language restrictions, fixed records and distribution-specific RNG. Japanese e-reader support is currently deliberately narrow.
7. **Completeness infrastructure:** resumable cross-profile/domain checkpoints, an explicit supported-domain certificate for exhaustive negative results, cancellation, progress estimates and duplicate-free result pagination. No timeout may be interpreted as global impossibility.

## Acceptance criteria for claiming completeness

- A reviewed inventory of acquisition variants, each mapped to a solver and verifier.
- Domain exhaustion proofs rather than merely successful examples or long random searches.
- Positive and negative fixtures per variant, plus malformed-proof and delivery-tampering tests.
- Independent differential checks against pinned legality references, with discrepancies investigated rather than silently filtered out.
- Performance and pause/resume tests on worst-case exact requests.
- Explicit licensing and provenance for every external data source; no ROM or reference-project resources bundled blindly.

Until these criteria hold, “impossible” is always scoped to the implemented model and any selected origin/acquisition filters. “Exhausted” means the current work budget ended. “Incomplete” means a proof or coverage boundary prevents an exhaustive conclusion. Exact user constraints are never relaxed automatically.
