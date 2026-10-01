> **Historical development record.** Version counts, compatibility and pending-work statements below describe the original FRLG work. Current three-game scope is in the [suite README](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md) and [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).

Current release status: see [FIXES.md](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/FIXES.md) for the September 27 cleanup, fixes and new validation. Older validation/checklist entries below are historical.

# Validation report

Date: 2026-09-27. Engine: official dev `84e076b2d1e2dda36073ff55ec7c311a6b97519c`. Interpreter: LuaJIT, built locally for this check; not bundled.

## Final checks

| Check | Result / scope |
| --- | --- |
| ROM-free per-mod behaviors | 26 mods × 2 editions = 52 passing suites, 336 assertions; covers enabled/disabled behavior, guards and relevant state changes. |
| Combined install | 2 passing suites: all 26 together for each edition, shared QOL entry, loader teardown, non-stacking reload, rejection on Red. |
| LegalMon coexistence | 2 additional passing loader/menu suites: all 26 plus the user's local LegalMon; both entries preserved, teardown/reload and overfull-menu paging. Not an end-to-end test of LegalMon generation. |
| Identical helper check | Every independent package carries identical support.lua bytes. |
| Existing imported FireRed data | 33 checks passed: actual metadata, item IDs, TM teaching, HM compatibility, summary/move/Dex panels, wheel and paged Start menu. |
| Existing imported LeafGreen data | The same 33 checks passed against that edition's own cache, not a copied FireRed fixture. |
| Native rendering | 16 local draw traces rendered using the installed editions' own fonts/chrome. Representative Summary, moves, Dex/evolution, guidance, wheel and Start menu inspected against LegalMon styling. These are static native-draw previews, not a full game recording. |
| Upstream regression baseline | 7 selected upstream scripts passed, none skipped; see list below. These run without the mod set and establish the adjacent engine baseline. |
| Upstream modkit | Each mod passes strict fixture validation, content lint, Gen 3 compatibility scan and packaging: 104 checks total. See check-results.json. |
| Distribution audit | Each archive contains source/documentation/manifest files only, safe relative paths and a manifest. Separate SHA-256 checksums supplied. |

The ROM-free suites use the real upstream loader and relevant engine routines with small synthetic fixtures and targeted mocks. They do not simulate every UI animation or full game session. The imported-data suites add actual engine data and rendering without copying assets into the deliverables or reading/writing any player save.

Selected upstream scripts: game3_bag_test.lua; game3_held_items_test.lua; game3_moveteach_relearner_test.lua; game3_storage_test.lua; game3_storage_pc_box_test.lua; game3_summary_controls_test.lua; game3_save_menu_layout_test.lua.

## Failures found and resolved during development

- PC batch-selection syntax error and a Lua toggle expression that could not deselect were corrected; selection/deselection/cancel now have regression checks.
- Reviewed native field names and corrected ghost-battle exclusion, berry pocket identity, nickname template, Ball aliases, type fields, item IDs, caught/owned Dex handling and PP maximum display.
- Test setup initially used absolute paths unsupported by the SDK filesystem, a missing legacy fixture dataset, and incomplete mocked species/render state. The harness now supplies the correct relative paths/data/stubs.
- The local LuaJIT build needed a macOS deployment target; modkit needed its explicit MODKIT_LUAJIT path. Imported-cache tests needed the Dataset.mountExtractRoots shim.
- Visual inspection caught wheel/footer overlap; layout was tightened before final packaging.
- Overcrowded Start menu rendering and native Help stealing the party-items L shortcut were corrected, with regression coverage.

No unresolved failure remains in the listed final checks. Nonfatal gen3check “unresolved” scan notes are retained in check-results.json: private wrapper targets passed as values are not followed by its static scanner. Fixture species-pack warnings and deliberately skipped Red targets are expected, not claims of testing imported data in those fixture suites.

## What is not verified

- No end-to-end interactive playthrough, real capture/save/restore session, controller-device test or long-running gameplay soak.
- No multiplayer/arena certification, arbitrary community-mod interoperability, every story/map state, every imported ROM revision, or later upstream beta.
- Imported-data checks do not validate all 26 gameplay features end-to-end. They focus on the data-dependent paths enumerated above.
- No engine patches, native widescreen implementation, full rebinding UI, universal timing scaler or expanded encounter availability model.

**Use with backed-up saves, offline, on the pinned revision first.** Restore a backup if testing causes unexpected persistent changes. Removing a mod does not reverse moves, names, item use or PC changes already saved.

## Reproduce

From this collection's directory, with the pinned upstream checkout at $UPSTREAM and a LuaJIT executable at $LUAJIT:

```sh
python3 tests/run.py --upstream "$UPSTREAM" --lua "$LUAJIT"
python3 tests/check_packages.py --upstream "$UPSTREAM" --lua "$LUAJIT" --pack
```

Optional imported-data checks (your own already-imported game data; no ROM included):

```sh
cd "$UPSTREAM"
"$LUAJIT" "$COLLECTION/tests/real_cache.lua" "$MODS_RELATIVE_TO_UPSTREAM" firered "$FIRERED_GBA_CACHE"
"$LUAJIT" "$COLLECTION/tests/real_cache.lua" "$MODS_RELATIVE_TO_UPSTREAM" leafgreen "$LEAFGREEN_GBA_CACHE"
```

Each cache variable points to that edition's data/generated/gba directory. The mod directory argument must be relative to the upstream checkout because the SDK filesystem is relative. An optional final argument writes private local draw traces; tests/render_trace.py renders them with Pillow. Do not redistribute the referenced extracted assets.

Optional LegalMon coexistence: from upstream, run tests/integration.lua with arguments `$MODS_RELATIVE_TO_UPSTREAM`, an edition, and `$LEGALMON_MOD_RELATIVE_TO_UPSTREAM`. LegalMon is not bundled; this extra test requires your separate source folder.

For the baseline scripts, set POKEPORT_GBA_CACHE to the existing FireRed data/generated/gba directory and run each listed script with LuaJIT from the upstream root. Check logs for SKIP as well as exit status.

## Manual smoke checklist before relying on a save

In each edition, test new-game shoes/indoor movement; text choices; cancelled/replacement TM teaching; all HM badge/terrain combinations; traded/egg rename guards; mushroom payment cancellation; Repel expiry through a warp/script; berry use followed by faint/switch/end; tutorial/Safari/ghost Ball restrictions; full/empty/stale PC batch targets; all wheel items and cancel; Surf by obstacles; Map/Fly transition input; key-item popup after a story script; save success/failure with a disposable save; and disable/restart of each package. These remain manual checks, not reported automated passes.
