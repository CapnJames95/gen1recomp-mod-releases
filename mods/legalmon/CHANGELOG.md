# Changelog

## [0.17.1] - 2026-09-27

- Trainer ID and Secret ID now open a controller-friendly numeric keypad with digits, DEL and OK. Letters, spaces and punctuation are ignored; entry is limited to five digits and retains the 0–65535 range check.
- Physical number-pad keys work, and navigation follows the three-column keypad. Names and searches retain their letter keyboard.
- Screen regression suite: 171/171 checks passed.

## [0.17.0] - 2026-09-27

- Added level-up teaching on the same level gain that triggers an ordinary level/friendship evolution. Separate acquisition and teaching bounds preserve the required level gain for each evolution.
- Capture at the evolution level cannot skip a level-up; consecutive level-up evolutions still require distinct gains. Stone/trade timing and earlier TM/tutor teaching remain unchanged.
- Applied the expanded timing to breeding-parent move histories, including learning at level 100 before evolving. Explanations show the teaching cutoff, which delivery reconstructs and checks.
- Added boundary combination, stale/tampered cutoff, capture timing and parent-history tests. Real-ROM tests exercise 139 species per FRLG host at newly supported teaching boundaries.
- Passed 44,126 automated checks and 19,203/19,203 independent encrypted PKHeX exports, including 278 new evolution-level teaching records.
- Special evolution methods, recursive parent PID/IV genealogy and broader documented gaps remain. No ROM assets or reference-project code/resources bundled.

## [0.16.0] - 2026-09-27

- Extended acquisition-bound pre-evolution teaching proofs to imported FRLG TM/HM and supported tutor compatibility, not just level-up/reminder moves.
- Earlier-stage machine/tutor sources are also available to breeding-parent chains, with explicit source categories in explanations. Each combination still uses one chronological path.
- Added positive combination, same-level stone teaching, already-evolved capture rejection, unsupported special-history, stale compatibility and tampered-proof tests. Removed ancestral TM/tutor permissions invalidate delivery.
- Passed 43,557 automated checks and 18,925/18,925 independent encrypted PKHeX regression exports. The expanded source handling did not change the encrypted records in this regression corpus; new focused coverage uses synthetic compatibility fixtures.
- Special evolution histories, same-level level-up teaching boundaries, recursive parent PID/IV ancestry and previously documented broader coverage gaps remain. No TM/tutor tables or other ROM assets bundled.

## [0.15.0] - 2026-09-27

- Added bounded, whole-moveset parent-chain proofs for FRLG egg inheritance. Every generation requires a compatible parent pair, with direct or inherited sources for all needed moves; circular chains cannot invent moves.
- Parent chains can retain supported pre-evolution level-up/reminder moves before later teaching and evolution. Proofs include chronological parent stages and are reconstructed before delivery.
- Added parental Smeargle Sketch sources backed by an imported catalog witness. Special battle setups, missing witnesses, Struggle and copying Sketch remain excluded; this is not an unrestricted Smeargle generator.
- Added cycle, incompatible-grandparent, state/depth-budget, Sketch witness, stale-source and nested-proof tampering tests. Real-ROM coverage exercises egg-list single-move and grouped requests, retaining explicit incomplete outcomes for unsupported cases.
- Passed 43,541 automated checks and 18,925/18,925 independent encrypted PKHeX exports. Native preview checked with a level-5 Bulbasaur carrying chain-inherited Charm.
- Limits remain explicit: 2,048 parent states, 16 ancestry levels, no shortest-chain guarantee, no recursive parent PID/IV genealogy, and no claim of exhaustive Gen III coverage. No ROM or reference-project resources bundled.

## [0.14.0] - 2026-09-27

- Added shared-parent level-up inheritance: an offspring can hatch knowing a later level-up move only when one compatible parent pair can directly supply it. Egg-list and shared moves are checked together, never pooled across different fathers.
- Added the female-counterpart breeding routes for Nidoran male and Volbeat, preserving existing offspring PID split-bit constraints.
- Added direct-source inheritance with Ditto in the mother slot and a breedable male/genderless parent from the offspring's own evolution family. This supports male-only cases such as Tyrogue without admitting arbitrary same-egg-group fathers.
- Reports identify both parent slots and maternal move sources. Delivery rechecks maternal and paternal sources and rejects modified proofs. No parents are consumed.
- Passed 39,517 automated checks and 15,453/15,453 independent PKHeX exports. No ROM data or reference-project source/resources bundled.
- Chained breeding, Sketch, earlier-stage-only parental move histories, recursive parent PID/IV ancestry, other source-game inheritance variants and broader acquisition/search gaps remain unfinished.

## [0.13.0] - 2026-09-27

- Added FRLG egg moves from the user's imported egg-move cache. The move picker respects acquisition filters; validation requires one compatible male father to supply every move requiring inheritance.
- Father sources are final-species FRLG level-up/reminder, TM/HM and supported tutor moves. Reports identify the hypothetical parent and move sources; delivery reconstructs the proof and rejects stale or altered parents.
- Chained breeding, Sketch, male-only/Ditto-parent inheritance, shared-parent level-up inheritance and recursive parent ancestry remain unmodeled. Unsupported combinations remain incomplete rather than falsely impossible; no exact request is relaxed.
- Passed 36,878 automated checks and 12,833/12,833 encrypted PKHeX regression exports, including 2,676 new egg-move records across both FRLG hosts.
- No egg-move tables, ROM assets or reference-project resources bundled.

## [0.12.0] - 2026-09-27

- Added acquisition-bound pre-evolution FRLG level-up/reminder moves for ordinary level, friendship, stone and trade evolution chains. Reports include chronological teaching/evolution stages.
- Move selection respects origin/acquisition filters. Already-evolved encounters cannot claim pre-capture teaching; stale or modified schedules fail delivery revalidation.
- Special evolution histories and same-level teaching/evolution boundaries remain conservative: unproven cases report incomplete rather than global impossibility. Egg moves and earlier-stage-only TM/tutor moves remain unfinished.
- Passed 34,185 automated checks and 10,157/10,157 encrypted PKHeX regression exports, including 156 new earlier-stage move-combination records across FRLG.
- No learnsets, ROM assets or reference-project code/resources bundled. Broader origins, rematches, events and parent histories remain documented gaps.

## [0.11.0] - 2026-09-27

- Added all nine active-edition FRLG NPC trades from the user's ROM cache, plus supported evolutions. Fixed PID, IVs, independent ability slot, trainer, nickname and contest data are preserved.
- Added a one-record validation domain instead of pretending trade records use Method 1 RNG. Exact conflicting traits and custom OT overrides fail; delivery rechecks the imported record.
- Trade met levels use a supported offered-species minimum. Does not consume offered Pokemon or trade flags; removable items/mail are omitted. Other-edition/RSE trades and every possible met level are not inferred.
- Added fixed-record, ability-parity, malformed-cache, stale-delivery and exact-request tests. All 33,853 checks and 10,001/10,001 encrypted PKHeX regression exports pass.
- No NPC trade tables, ROM assets or reference-project code/resources bundled. Remaining source-game, event, rematch and move/parent-history gaps stay documented.

## [0.10.0] - 2026-09-27

- Added all 28 Unown forms with exact-form selection, imported chamber/slot checks and form-specific PID rejection proofs. Missing chamber data and mismatched requests fail closed.
- Added native form-picker previews and PID-correct result artwork; saved builds preserve the form and species changes clear Unown-only constraints.
- Added Cape Brink ultimate tutor moves through the host's species rules, with generated friendship 255 and explicit provenance. Does not consume tutor flags.
- Passed 33,662 automated checks and 9,949/9,949 encrypted PKHeX regression exports. Inspected native rendered Unown question-mark preview and exclamation-mark picker artwork.
- No ROM assets or reference-project source/resources bundled. RSE wild sources, alternate rematches, parent/move histories, cartridge trades and remaining events are still unfinished.

## [0.9.0] - 2026-09-27

- Added Method H2/H4 variants for imported ordinary FRLG wild encounters, without applying them to statics, gifts or Unown. Exact-IV anchors and perfect finders use each variant's RNG ordering.
- Added independent forward replay tests for PID rejection chains, skipped IV calls, encounter levels, perfect anchors and tampered proofs. Diagnostics distinguish method-specific impossibility from global failure.
- Added the 15 standard FRLG tutors from the user's imported cache, with labeled move-picker entries, source reports and fresh delivery validation. Missing/unknown tutor data fails closed. Cape Brink ultimate moves remain unsupported.
- Passed 33,140 automated checks and 9,891/9,891 exported encrypted records through the pinned PKHeX checker, including H2/H4 wild samples and compatible tutor move batches on both hosts.
- No ROM assets, tutor compatibility tables or reference-project code/resources bundled. Alternate rematches, RSE wild sources, broader move histories and remaining events are still unfinished.

## [0.8.0] - 2026-09-27

- Added round-robin validation across every eligible implemented acquisition profile, preserving per-profile cursors on pause/resume. An early impossible route no longer blocks later legal origins.
- Selected-profile delivery re-prepares against the trusted current catalog and exact request. Added profile-index, forged-profile, changed-filter and duplicate-delivery regression checks.
- L/R browsing and shiny/perfect finders consider alternate profiles; identical PID/IV/ability/OT/language outcomes are deduplicated. Snapshot copying preserves internal sharing without sharing mutable state with previous results.
- Exposed explicit FRLG egg routes alongside existing static/wild routes, including evolution paths and non-incense Marill/Wobbuffet. Added an egg acquisition filter; parent ancestry and egg moves remain outside scope.
- Passed 26,966 automated checks and 7,827/7,827 freshly exported encrypted records through the pinned PKHeX checker. No ROM assets or reference-project code/resources added.
- Updated the coverage audit: alternate rematches, broader moves/events, RSE wild methods and exhaustive parent histories are still unfinished. This is not exhaustive Gen III legality coverage.

## [0.7.1] - 2026-09-27

- Replaced blocking Poké Spot PID validation with an incremental, resumable stage and explicit PID/IV progress labels.
- Added exact GameCube PID reversal, checked against brute-force state suffix enumeration. Shiny PID searches cover all 524,288 possibilities for fixed trainer IDs; ordinary PID searches can traverse the full RNG period.
- Stopped treating exhaustion of IV anchors for one Poké Spot PID as proof that every PID/IV combination is impossible, including preview pagination messages.
- Added a coverage audit separating implemented finite domains from remaining encounter, move, parent-history and cross-profile gaps. This release does not claim exhaustive Gen III legality.
- Passed 23,797 automated checks and all 6,270 encrypted-record PKHeX regression checks. No game assets or reference-project code/resources added.

## [0.7.0] - 2026-09-27

- Added all remaining XD Shadow species: 83 total. Forward NPC team simulation covers traits, preceding Shadows and CPU/player anti-shiny PID rerolls; Colosseum no longer depends on first-roll-only proofs.
- Added all nine Poke Spot species with separate activation/PID and animation/IV/level proofs, including shiny and perfect-IV searches.
- Added Japanese e-Reader Togepi/Mareep/Scizor and evolutions with fixed zero IVs, locked traits, purification and explicit language/nickname handling.
- Expanded naming-screen proofs to ball-spawn branches and added an exact acquisition-route picker.
- Documented bounded searches, special OT/name requirements and alternate-rematch scope. No ROM assets, Japanese species-name table or PKHeX code/resources are bundled.
- All 6,270 encrypted regression exports pass the pinned independent PKHeX checker on the combined FRLG test set.

## [0.6.0] - 2026-09-27

- Added purified routes for all 48 regular Colosseum Shadow species. Makuhita/Gligar/Ursaring use bounded, independently replayed first-roll team proofs; unsearched rejection branches are reported as incomplete, not impossible.
- Expanded XD to twelve no-lock Shadow species, including Lugia, plus supported evolutions.
- Added ID-correlated Colosseum Espeon/Umbreon and XD Eevee starters. Exact OTs are never rewritten; starter searches enumerate the supported ID-derived seeds.
- Added Colosseum Plusle and XD Elekid/Meditite/Shuckle/Larvitar NPC gifts/trades, preserving required identity, nickname, SID semantics and shiny restrictions.
- Kept XD team locks, Poke Spots, e-reader and additional naming/rejection branches blocked. No blanket GameCube-completion claim.
- Both FRLG caches pass; 4,960 encrypted exports independently pass the pinned PKHeX checker. Added starter, team-lock, fixed-OT and nickname regressions.

## [0.5.0] - 2026-09-27

- Added selected Colosseum/XD purified Shadow routes without preceding-team locks, plus XD Mt. Battle gifts and supported evolutions. Other GameCube encounters remain blocked.
- Implemented GameCube RNG, independent ability slots, XD Shadow shiny rerolls, National Ribbon/fateful flags, exact IV search and both finders.
- Added editable original trainer name, gender, TID/SID and a reviewable random draft. Fixed-event OTs remain immutable; changed OTs require revalidation.
- Added conservative GameCube name-screen/trainer-ID proofs and Ruby/Sapphire trainer-ID correlation checks. Unsupported exact IDs fail closed.
- Added RNG, OT, UI and real-ROM regressions. Independently checked 4,410 encrypted exports with the pinned PKHeX reference; all passed.

## [0.4.3] - 2026-09-27

### Changed
- Selecting a Pokémon from the species picker/search sets its lowest supported acquisition/evolution level for the current origin filter, raising or lowering the previous level as necessary. Other constraints remain unchanged and old validation is cleared.
- Unsupported species/origin pairs keep the previous level and still fail validation; manual level changes remain available afterward.

## [0.4.2] - 2026-09-27

### Added
- SELECT in validated previews/comparisons jumps to the highest six-stat IV total among the current cached results, keeping the first result on ties. Shows the total out of 186 and a visible control hint.
- Pauses an active next-result search without losing its cursor. Does not reorder results, relax constraints, regenerate consumed proofs or claim a global optimum over unsearched seeds. Initial-validation SELECT still cancels.

## [0.4.1] - 2026-09-27

### Fixed
- Species picker header shows the selected Pokémon's National Dex number, including filtered results and Hoenn's remapped internal IDs. Search, Clear filter and No matches controls have no Pokémon number; other menu position counters are unchanged.

## [0.4.0] - 2026-09-27

### Added
- Verified generating paths for all 386 Gen III species in both FRLG editions, not just a complete species picker.
- FRLG hatched-egg generation for missing breedable species: pending PID, compatible-parent check, collection PID/IV RNG and three distinct inherited stats with parent slots. Reports expose hypothetical-parent assumptions and incense requirements.
- Wurmple personality branches, Tyrogue stat branches, Ninjask/Shedinja evolution and Milotic beauty/sheen metadata.
- FRLG roaming beasts with the retail IV truncation bug, Emerald roaming Latias/Latios, and Unown A's high-first PID/letter-rejection proof from Monean Chamber.
- Event-ticket Lugia/Ho-Oh/Deoxys plus restricted English Aura Mew, 10 ANIV Celebi and WISHMKR Jirachi distributions. Correct event OT/IDs/gender, fateful metadata and shiny locks are retained and shown before delivery.
- All-31 finder supports bounded egg samples and finite event domains; current-seed finders use the acquisition-specific algorithm. Event shininess uses event IDs.

### Validation and scope
- All 386 generated and cartridge-round-tripped on each host; 3,910 exported samples passed pinned PKHeX legality and checksums, including advertised minimum levels and shiny WISHMKR.
- Native breeding inheritance cross-checks, independent Unown forward replay, special-evolution and event constraints, fixed-OT preview and finite-domain navigation tests.
- All species does not mean every form, event or origin. Egg parents are hypothetical; their ancestry is not recursively reconstructed. No encounter progress/history is claimed or changed.

## [0.3.0] - 2026-09-27

### Added
- Origin selection: any supported, FireRed, LeafGreen, Ruby, Sapphire or Emerald; exact origins are never silently relaxed.
- Supported RSE non-event starters, fossils, gifts and stationary encounters, plus transfers from either FRLG edition's static/gift paths.
- ROM-derived FRLG land, surf, Rock Smash and all three rod encounter tables, including Safari Ball metadata. Method H1 proofs replay slot, met level, nature selection and rejected PID pairs.
- Supported level, stone, trade, trade-item and friendship evolution paths into Gen III species.
- Actual source game, encounter method, met level and wild reversal proof in previews and reports.
- Independent forward/reverse wild fixtures and optional PKHeX conformance checker. All 1,034 exported test records passed pinned PKHeX legality and checksums.

### Scope and safeguards
- Tested generation coverage: 208 species with the FireRed cache, 209 with LeafGreen. All 386 remain browsable, but full all-species generation is not implemented.
- Unown, Altering Cave, H2/H4, eggs, events, roamers, NPC trades, GameCube and unsupported special evolutions remain blocked.
- A bounded wild reversal is reported as incomplete, never exhaustive impossibility; finite IV-anchor searches cannot be extended past their state space.
- No ROM assets, encounter tables, exported Pokémon, PKHeX resources or binaries are included in the release.

## [0.2.1] - 2026-09-27

### Fixed
- Prevent the engine's global Help and L=A handling from intercepting LegalMon shoulder navigation while its modal owns input; restore the prior Help context afterward.
- L now goes back in menus and cancels text editing. Preview/comparison L/R still select previous/next results; B returns from those screens.

### Changed
- Reduce the home menu to six entries: Configure Pokemon, Validate, Preview & send, Finders & tools, Results & style, Close.
- Group configuration and utility screens without removing existing features or changing legality scope.
- Browse all 386 Gen III species in National Dex order using ROM mappings. Unsupported generation origins are marked `[!]` and fail closed. This is a catalog expansion, not full cross-origin generation support.

## [0.2.0] - 2026-09-27

### Added
- Side-by-side IV/stat comparison, signed differences, native shoulder-button hints, up to eight removable/restorable result pins.
- Explicit trait/IV locks for rerolling; actionable all-31 nature, shiny and Hidden Power diagnostics.
- Zero Attack/Speed, five-perfect and minimum-total IV constraints; Gen III Hidden Power type/power filtering and reports.
- Grouped species results, numbered spreads with nature/gender/shiny badges and ability/seed details.
- Shiny-only result filtering and any-supported-species shiny finder using an exact read-only live-seed snapshot.
- Box targeting with free-slot preview, full-box failure without spillover, and no overwrites.
- Last configuration, search filters, cursor positions and style settings restored without persisting generation proofs.
- Optional selection cries, optional ROM-sprite bounce, and validation status indicators.

### Validation
- Synthetic solver/UI/PC tests, engine Hidden Power cross-checks, native-ROM rendering and optional imported FRLG cache tests. No ROM assets bundled.

## [0.1.0] - 2026-09-26

### Added
- All-31 finder: exact live-seed snapshot, all-seed species/nature options, and strict keep-my-choices search; explicit change review and normal delivery guards.
- L/R browsing of validated matching results, with visible controls and resumable next-result search.
- All minimum 20 IV shortcut, applied to all six stats after confirmation.
- Native FRLG start-menu screen, strict Method 1 constraints and resumable searches.
- Non-event static/gift acquisition paths, ROM-derived moves and supported evolutions.
- Explained validation and guarded party/PC generation.
- Native frames, ROM font and normal/shiny front sprites, typed/controller search, presets and IV shortcuts.
- Live compatibility hints, explicit alternatives, search pause/resume/cancel, confirmation preview and capacity display.
- Named favourites, recent builds, and exportable plain-text legality reports.
