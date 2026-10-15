# v1.5.0 validation — 13 October 2026

The release includes the latest Safari/travel/QoL sources and the engine 0.3.85
roamer compatibility fix. The suite contains 35 components, 34 applicable per game.

- 215 source startup probes against the official 0.3.85 engine (43 packages × five games): 212 completed without errors. The three Hoenn suite probes reach Key Item Help's imported-item-cache requirement, which the data-free harness cannot satisfy.
- Regression checks cover all nine shared helper copies, legacy and modern roamer APIs, all five games, co-loading, legacy PID/IV RNG consumption and preservation of the modern engine's native functions.
- 417 Lua source files parsed successfully before release packaging.
- All eight extracted ZIPs pass strict modkit validation and content lint. An additional 40 packaged startup probes yield 37 clean results and the same three cache-dependent suite probes.
- Publication checks validate all eight installable archives, source identity, version/hash metadata, local documentation links and the matching manual-install bundle.

These are startup and regression checks, not a full gameplay, Android, touch or
export-legality validation. The new Safari, teleport, zoom and collision features
have not received an exhaustive hardware playthrough. Retained screenshots show
earlier builds; no new screenshot coverage is claimed for the three added tools.

See [engine compatibility details](engine-0.3.85-compatibility.md) and
[screenshot provenance](SCREENSHOTS.md).

## Earlier v1.4.0 evidence (not rerun for v1.5.0)


## LegalMon 0.18.3

All 386 species have a supported route in each of FR/LG/E/R/S. 235,871 minimum-level acquisition profile samples and 12,415 level-100 species/origin samples passed PKHeX (248,286 total). No source-supported transfer pairs were missing with all five supported ROMs imported. Full source catalogue expansion requires the source ROM to be imported locally; Ditto has a built-in transfer fallback. 2,672 unit checks passed.

## Shiny Hunter 0.3.4

520 stationary-encounter and 500 starter/gift/roamer/hatched-egg samples passed PKHeX. Tests cover default/disabled/stale-loader RNG preservation, fixed PID exclusions, complete PID/IV rolls, pending-egg handling, inheritance and single delivery. Relevant generation files are identical between the tested Mac 0.3.56 and Thor 0.3.57 payloads.

On Thor, controlled Ruby runtime checks generated and delivered Ditto through LegalMon and generated, displayed and captured a 1/1 shiny Rayquaza. Both device exports passed PKHeX. These were instrumented runtime checks, not a complete manual walkthrough of the Sky Pillar story. Temporary diagnostics were removed; original saves, settings and mod storage were restored byte-for-byte. Installed mod files were verified.

## Packaging and limits

All eight packages passed strict modkit validation and lint. ZIP contents exclude macOS metadata, ROM caches, player saves, generated Pokémon and test tooling. The complete manual-install bundle is verified against its individual archives. The abandoned native berry-list workaround is absent.

Automated analyzer acceptance is not exhaustive legality or gameplay validation. Existing Pokémon are not rewritten by shiny odds; select odds before generation (before egg production in Emerald). Fixed events remain controlled by their own distributions.

Dual Screen odds produced 500/500 shiny encounters across the five games at 1/1; the hold-L override produced 100/100 with saved odds Vanilla and the toggle OFF. All 600 exports passed PKHeX. Menu visibility, inline toggling, disabled defaults and saved-setting preservation were checked.


## Reusable TM fix (0.3.14)

Reproduced consumption with the released 0.3.13 component in all five games. Native-data automated regressions on engine 0.3.56 cover party-menu immediate teaching, replacement completion callbacks, cancellation, ordinary item removal and feature OFF; the fixed component passed all five games. Engine 0.3.85 source retains the same bypassing party-menu path. Presentation/choice UI is stubbed; this is not a full manual gameplay pass on 0.3.85.


## Repel reuse movement fix (0.3.15)

Reproduced the released component leaving the native step-event queue busy after Yes/No in all five games. Automated native-data regressions on engine 0.3.56 now pass for Yes, No, B/back, empty bags, disabling while open, repeated prompts and subsequent field events. Only the native wore-off text is automatically dismissed; the reuse menu and event queue execute normally. Strict modkit validation and lint pass. This is not a new manual hardware or full latest-engine gameplay validation.
