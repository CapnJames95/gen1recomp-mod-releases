# v1.4.0 validation

## LegalMon 0.18.3

All 386 species have a supported route in each of FR/LG/E/R/S. 235,871 minimum-level acquisition profile samples and 12,415 level-100 species/origin samples passed PKHeX (248,286 total). No source-supported transfer pairs were missing with all five supported ROMs imported. Full source catalogue expansion requires the source ROM to be imported locally; Ditto has a built-in transfer fallback. 2,672 unit checks passed.

## Shiny Hunter 0.3.4

520 stationary-encounter and 500 starter/gift/roamer/hatched-egg samples passed PKHeX. Tests cover default/disabled/stale-loader RNG preservation, fixed PID exclusions, complete PID/IV rolls, pending-egg handling, inheritance and single delivery. Relevant generation files are identical between the tested Mac 0.3.56 and Thor 0.3.57 payloads.

On Thor, controlled Ruby runtime checks generated and delivered Ditto through LegalMon and generated, displayed and captured a 1/1 shiny Rayquaza. Both device exports passed PKHeX. These were instrumented runtime checks, not a complete manual walkthrough of the Sky Pillar story. Temporary diagnostics were removed; original saves, settings and mod storage were restored byte-for-byte. Installed mod files were verified.

## Packaging and limits

All eight packages passed strict modkit validation and lint. ZIP contents exclude macOS metadata, ROM caches, player saves, generated Pokémon and test tooling. The complete manual-install bundle is verified against its individual archives. The abandoned native berry-list workaround is absent.

Automated analyzer acceptance is not exhaustive legality or gameplay validation. Existing Pokémon are not rewritten by shiny odds; select odds before generation (before egg production in Emerald). Fixed events remain controlled by their own distributions.

Dual Screen odds produced 500/500 shiny encounters across the five games at 1/1; the hold-L override produced 100/100 with saved odds Vanilla and the toggle OFF. All 600 exports passed PKHeX. Menu visibility, inline toggling, disabled defaults and saved-setting preservation were checked.
