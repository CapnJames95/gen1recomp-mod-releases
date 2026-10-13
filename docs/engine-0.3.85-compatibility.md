# Engine 0.3.85 compatibility fix — 13 October 2026

Applied to the latest collection branch, including Shiny Hunter 0.3.6,
Gen3DualScreen 0.4.18 and the 35-component QoL Suite 0.3.13.

The native legality helper assumed every engine exposed `Roamer.generateMon`.
Engine 0.3.85 moved generation inside the roamer module and exposes native
instance construction instead. The unconditional assertion prevented Shiny
Hunter, Encounter Reset, Encounter Tour, Dual Screen, Day Care Viewer and
Pokémon Services from starting, including on Hoenn games.

The helper now installs its legacy generation and encounter-descriptor wrappers
only when `generateMon` exists. Modern engines retain their own roamer handling;
older engines retain the FRLG correction. Other compatibility checks remain
strict. All six standalone callers, both bundled copies, the canonical helper
and the suite's component hashes are synchronized.

## Validation

- Regression test: all nine helper copies match; legacy and modern API shapes
  across all five games; co-loading does not stack wrappers; legacy PID/IV RNG
  draws and truncation; disabled owners delegate; Hoenn bypasses FRLG corrections;
  modern functions and descriptors remain untouched.
- Actual 0.3.85 loader: 43 source packages × five games = 215 startup probes.
  212 completed without errors. Three suite probes (Emerald/Ruby/Sapphire) reach
  Key Item Help's imported-item-cache requirement, which this data-free harness
  cannot satisfy. None reports the removed roamer API failure.
- Startup tests do not establish complete gameplay, Android UI or export legality.

The fix is included in the v1.5.0 individual downloads and manual-install bundle.
Earlier v1.4.0 assets remain available in their historical release.
