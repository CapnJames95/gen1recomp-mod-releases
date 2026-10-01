# Hoenn Tools 0.1.1

An Emerald-only companion included in **QoL Suite 0.3.1** for gen1recomp 0.3.39. Open **START → QOL → HOENN TOOLS**, or the **HOENN TOOLS** Home tile in Gen3DualScreen 0.4.3. Dual Screen is optional. FireRed and LeafGreen hide this component.

| Tool | Features |
| --- | --- |
| Match Call | Ready trainers and Gym Leaders, with native map locations. The existing Match Call shortcut opens this expanded view when available. |
| Berry garden | Growing trees sorted with harvests first, native berry names, map coordinates, growth stage, minutes to the next stage, watering status and harvest yield. Select a tree, then **Teleport to berry tree** to land on foot beside it, facing it. Water or harvest normally. Refuses blocked landings, active challenges, battles, scripts and movement. |
| Battle Frontier | BP, silver/gold symbol count, current/best streaks by facility, mode and level category, facility rules and a selectable three-Pokémon basic entry check. Factory uses rentals. Native reception remains authoritative, particularly for Multi/Double entry sizes. |
| Feebas assistant | Identify the tile you face on Route 119 and mark/unmark searched tiles. Optional valid-spot reveal is OFF by default. Marks are saved with the playthrough and separated by Dewford seed. Open Shiny Hunter from this panel to configure a normal fishing hunt. |
| Contest / Pokéblock planner | Party condition and sheen, favourite flavour, previews for owned Pokéblocks, current move categories, appeal/jam, descriptions and available follow-up combinations. Previewing never feeds a Pokémon or consumes a block. |
| Bike switch | The **Bike: Mach/Acro (A: switch)** row switches an owned bike immediately without opening another screen. Its registration follows the swap. Retain riding state where native bike rules permit. Refuses rails, bumpy slopes, Cycling Road, underwater/surfing and active challenges. Obtain a bike from Rydel normally first. |
| Daily events | Native game clock, Shoal Cave tide and next transition time, today's Mirage Island party eligibility, and current Terra/Marine Cave route information. No clock or encounter manipulation. |
| Secret base tools | Recorded base locations, registration, owner's daily battle status, placed decorations and owned decoration inventory. Manage registrations with a safe remote list and confirm before removing one. Empty-list and Back actions never run base-PC scripts. Decoration arrangement requires facing the PC inside your own base. |

Use **Up/Down** to select, **A** to open, **B** to return, and **Left/Right** to page. Dual Screen supplies the existing touch row/page controls. Feebas reveal is under **QOL SETTINGS → Hoenn Tools → SELECT**.

Reading panels does not advance encounter RNG. Information is calculated when a panel opens, with no permanent per-frame scans. Feebas marks are user notes: an unsuccessful fishing attempt does not establish that a tile cannot produce Feebas. Bike exchange and native base management retain activity/session checks.

These are native menu renders using synthetic state, not hardware gameplay screenshots:

![Hoenn Tools settings](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_hoenn_tools-options.png)

![Hoenn Tools menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/hoenn-tools-home.png)
![Berry garden](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/hoenn-tools-berries.png)
![Berry location and harvest](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/hoenn-tools-berry-detail.png)

Automated checks cover native imported data, all eight entry panels, Feebas/native-rule agreement across 446 fishing tiles, seed-specific marks, preview isolation, rematch locations and guarded bike exchange. Gameplay validation is deferred at the owner's request. Thor performance was reported excellent before this feature update; this update still needs manual device verification.
