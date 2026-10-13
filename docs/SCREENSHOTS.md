# Screenshots and preview provenance

All retained gallery images are **historical examples** captured before v1.5.0.
They may illustrate unchanged features, but are not evidence of current labels,
layouts, version numbers or new feature coverage. The folder name `current/` is a
legacy path retained to preserve links.

Native renderer previews use synthetic test state and locally imported assets;
they are not AI mockups or new hardware gameplay captures. The earlier Thor image
is a hardware screenshot. No new hardware coverage is claimed for Safari Tools,
Zoom Controls, Walk Through Walls or the expanded Teleport menus.

The [image audit](screenshot-audit.json) preserves capture-build metadata and
records image hashes separately from current release versions. See the
[gallery index](RELEASE-SCREENSHOTS.md) and [current validation](latest-validation.md).

## Historical gallery

## Shared Home layout

Emerald, pages 1–4:

![Emerald Home layout](screenshots/current/emerald-home.png)

FireRed, pages 1–4; the same shared defaults apply to LeafGreen:

![FireRed Home layout](screenshots/current/firered-home.png)

These previews use the earlier shared preset. Game-specific unavailable shortcuts are omitted; other tiles retain their coordinates. Squirt Bottle and Headbutt are hidden. Rods/bike actions and field shortcuts use compact rows.

## Emerald navigation

These refreshed captures show the full native screen below the companion toolbar. The Emerald Home tile opens PokéNav; FR/LG keep MAP. Both are synthetic render previews, not Thor gameplay recordings.

| PokéNav | Town Map |
| --- | --- |
| ![Native PokéNav](screenshots/current/emerald-pokenav.png) | ![Native Town Map](screenshots/current/emerald-town-map.png) |

## Earlier mod menus

The companion renders the actual native mod menu. The paged footer shows **PREV PAGE / NEXT PAGE / BACK**. Each tool also works through its ordinary game menu without Dual Screen.

| Mod | Emerald | FireRed |
| --- | --- | --- |
| LegalMon | [Preview](screenshots/current/emerald-legalmon.png) | [Preview](screenshots/current/firered-legalmon.png) |
| Event Distributions | [Preview](screenshots/current/emerald-event-distributor.png) | [Preview](screenshots/current/firered-event-distributor.png) |
| Shiny Hunter | [Preview](screenshots/current/emerald-shiny_hunter.png) | [Preview](screenshots/current/firered-shiny_hunter.png) |
| Auto Breeder | [Preview](screenshots/current/emerald-autobreeder.png) | [Preview](screenshots/current/firered-autobreeder.png) |
| Encounter Tour | [Preview](screenshots/current/emerald-encounter_tour.png) | [Preview](screenshots/current/firered-encounter_tour.png) |
| Encounter Reset | [Preview](screenshots/current/emerald-encounter_reset.png) | [Preview](screenshots/current/firered-encounter_reset.png) |
| Pokémon Services | [Preview](screenshots/current/emerald-pokemon-services.png) | [Preview](screenshots/current/firered-pokemon-services.png) |
| Day Care | [Preview](screenshots/current/emerald-daycare-viewer.png) | [Preview](screenshots/current/firered-daycare-viewer.png) |
| Teleport | [Preview](screenshots/current/emerald-fly-teleport.png) | [Preview](screenshots/current/firered-fly-teleport.png) |

![Current mod-tool footer](screenshots/current/emerald-legalmon.png)

## QoL, starters and Hoenn

- All **32 suite component detail pages and their available options pages** were regenerated. These show actual component names, versions and option schemas in the native manager. The installed distribution remains the combined suite; they do not imply standalone downloads. The manager truncates long labels and uses a four-row options viewport.
- The suite's [31 applicable feature switches](screenshots/qol-suite-menu.png), [Field Kit options](screenshots/qol-suite-options.png), [shortcut list](screenshots/qol-suite-shortcuts.png) and [binding context](screenshots/qol-suite-shortcut-context.png) were refreshed.
- [Quick Field Actions](screenshots/frlg_qol_auto_surf-detail.png) now shows the current name instead of Auto Surf Prompt.
- [Emerald starter-repeat menu](screenshots/encounter-reset-emerald-starters-detail.png) and [FRLG starter-repeat menu](screenshots/encounter-reset-firered-starters-detail.png) show Prepare repeat starter / Collect prepared starter. These demonstrate the menu, not a completed collection or a new PKHeX result.
- Hoenn Tools: [Match Call](screenshots/hoenn-tools-match-call.png), [berry patches](screenshots/hoenn-tools-berries.png), [berry teleport/details](screenshots/hoenn-tools-berry-detail.png), [Frontier](screenshots/hoenn-tools-frontier.png), [Feebas](screenshots/hoenn-tools-feebas.png), [contest](screenshots/hoenn-tools-contest.png), [inline bike switch](screenshots/hoenn-tools-bike.png), [daily events](screenshots/hoenn-tools-daily-events.png), [Secret Bases](screenshots/hoenn-tools-secret-bases.png). Empty-party/base/rematch examples are intentional synthetic states.
- Start-menu ordering and folders remain current. Size/position editor images are historical: that feature was removed in Suite 0.3.9.
- Dual Screen Home pages, collection panels, startup and options were refreshed for 0.4.14. New Emerald PokéNav and Town Map captures show the isolated companion viewport.
- QoL effect previews were regenerated for Summary values, Dex/evolution, item help, held items, nickname entry, move reminder, Repel reuse, shop owned counts, bag sorting and VS Seeker charge.

## Reproduction

`tools/docs-preview/` renders shared Home pages and collection menus through LÖVE using the current combined suite. Set `KANTO_GEAR_HOST_PATH`, `KANTO_GEAR_MOD_PATH`, `KANTO_GEAR_PREVIEW_OUTPUT` (output filename prefix), `FRLG_COLLECTION_PATH`, `FRLG_QOL_COMBINED=1`, `FRLG_QOL_SUITE_ROOT` (absolute collection path without its leading slash), `POKEPORT_VERSION` and `POKEPORT_GBA_CACHE`. Run the preview folder with LÖVE from the host checkout. The preview creates synthetic sessions and never loads a player save.

Other retained current capture helpers:

| Helper | Coverage |
| --- | --- |
| `tools/capture-qol-manager.lua` | Component detail/options schemas |
| `mods/frlg-qol-suite/tests/capture.lua` | Combined suite settings and shortcuts |
| `tools/capture-qol-effects.lua` | Native QoL effects; retired move-details/battle-hints captures removed |
| `tools/capture-scrollable-start.lua` | Current native Start organiser, ordering and folders |
| `tools/emerald-port/capture-hoenn.lua` | Eight Hoenn entry panels and berry patch detail |
| `tools/emerald-port/capture-encounters.lua` | Current Tour/Reset menus, including native starter-row definitions |
| `tools/frlg-dual-screen/startup_preview/` | Current startup branding |
| `tools/frlg-dual-screen/portable_preview/` | Compact actions and Emerald owned/wild IV display |
| `tools/frlg-dual-screen/tile_settings_preview/` | Current Home visibility options |
| `tools/start-menu/preview/` | Historical size/position editor (removed) |

The trace helpers take source root, edition, imported cache directory and output trace directory; use `tools/render-manager-traces.py` to composite their draw operations. Manager/effects helpers expect the canonical `qol/mods` path; the suite helper expects the collection path without its leading slash; Hoenn/encounter helpers expect the collection root. All caches remain local.
