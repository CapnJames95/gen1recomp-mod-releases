# Upstream and community review

## Official project inspected

- [Official repository](https://github.com/bryanthaboi/gen1recomp), dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`.
- [Official wiki](https://github.com/bryanthaboi/gen1recomp/wiki), checkout `4ef9696897a3f9bb787802d7171401f12f7e0d8b`: mod object, hooks/events, lifecycle, registries, compatibility, modding basics and modkit.
- [Official examples](https://github.com/bryanthaboi/gen1recomp/tree/84e076b2d1e2dda36073ff55ec7c311a6b97519c/mods/examples): API-2 entry points, manifests, event/hook and registry patterns.
- [Official mod index](https://github.com/bryanthaboi/gen1recomp-mod-index), checkout `f4dd0d053cfde20f4b95dc31aade1ef02597907f`.

The actual FRLG implementation was treated as authoritative when generic wiki examples targeted Gen 1. Inspected modules include Game3, Gen3Compat, Loader, WorldAPI, game3 player/field moves/battle/items/storage, native UI stack and menus, option rows, and the upstream tests.

## Existing concepts, not claimed inventions

| Community project / index entry | Overlap considered |
| --- | --- |
| [FAFF0x collection](https://github.com/FAFF0x/gen1recomp) | Reusable machines, HM access, renaming, modern Bag/battle/Dex ideas. |
| [KuroKratos collection](https://github.com/KuroKratos/gen1recomp-mods) | Broader modern QoL concepts. |
| [MadeinTaly Running Shoes](https://github.com/MadeinTaly/gen1recomp-running-shoes) | Running/speed; index describes Gen 2 support. |
| [Wild Gen1ModernBag](https://github.com/wild1walker/Gen1ModernBag) | Sorting, pockets, favorites and TM/HM conveniences; index credits FAFF0x. |
| Official index: anytime_rename, move_descriptions | Menu rename and move-information concepts. |
| Official index: useful_bag, Gen1BillsBox, instant_heal_pc_rest, qol_toggles | Bag sorting, PC controls, healing speed and centralized toggles. |

Review was conceptual and based on public descriptions/index metadata and repository overviews, not a complete security audit or a claim of testing those mods. Existing concepts were not duplicated blindly: native FRLG equivalents were left alone, while the shipped replacements target actual FRLG modules, preserve edition routing, avoid Gen 1 data assumptions, and stay independently installable.

No community mod source, ROM assets, extracted tables or game graphics were copied into these packages. LegalMon's visual reference came from the user's other local chat/artifact; only the requested layout/palette conventions were matched. Its files were not edited.

## Architectural choices

- API 2, explicit firered/leafgreen targets, declared engine_internals permission.
- Narrow wrapper chains instead of editing the engine or imported scripts.
- Wrapper activation bound to the current loader event bus and game version; reload reuses a keyed wrapper instead of stacking copies.
- Only read-only data views where a deeper mutation would be unsafe.
- Native item teaching, payment, battle actions, field checks, saving, and callback paths retained.
- All new custom panels use one byte-identical LegalMon-style helper copied into each independent package.
- Private APIs still entail compatibility risks; modkit's “will load” is not a gameplay guarantee.
