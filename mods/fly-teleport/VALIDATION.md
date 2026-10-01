# Fly Teleport validation — 2026-09-27

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


Host: official Gen1Recomp checkout `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. Tests use synthetic sessions and the user's imported caches; no player save is opened or modified.

- Native engine test: **291 checks per edition**, FireRed and LeafGreen. Exact coverage of all 20 imported Fly destinations, unique entries, native coordinates and successful warps, party/money preservation, walking state, occupied/missing landing rejection, movement/locked/link rejection, unknown destinations, START registration, Cancel default, cancellation, success closure and disabled confirmation rejection. Also covers all 20 native visited flags (numeric, named and live script stores), read-only unlock checks, progression as the default, locked-row messaging, live unlocks, stale confirmations, mode changes and the manager persistence path.
- Dual Screen collection suite: **362 checks per edition**. Includes the new tile, real native menu launch, companion routing, disabled/uninstalled visibility and refusal to launch stale tiles, re-enable restoration and duplicate prevention.
- Modkit validate, lint and gen3check pass for Fly Teleport and Dual Screen. Dual Screen retains its existing compatibility warnings; static checks do not replace runtime tests.
- Native FRLG draw traces for the destination list, Sevii list and confirmation rendered and visually inspected.

Reproduce from the engine checkout using `/path/to/luajit /path/to/collection/tools/fly-teleport/engine_test.lua`, setting `TELEPORT_MOD` to the mod directory, `POKEPORT_VERSION` to `firered` or `leafgreen`, and `POKEPORT_GBA_CACHE` to that edition's imported cache. Logs are under `tools/fly-teleport/results`.

Physical Android/AYN Thor testing and full story playthroughs remain unverified. Progression is the default; only optional All unlocked mode bypasses destination locks. Normal native arrival scripts remain active.
