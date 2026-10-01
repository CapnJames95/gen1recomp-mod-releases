# Reorganization verification — 0.2.1

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


Rechecked 27 September 2026 against local host `fab224458f9d5af79a82b5ff5338347ef74c0189` with LuaJIT. Updated and rechecked the A-pickup, Up/Down-move, A-place interaction.

## Results

- `tests/runtime.lua`: PASS for both editions. Menu sizing, overflow, callback selection, wrapping, confirmation, Safari, renderer ordering, disabling, teardown and error restoration.
- `tests/organizer.lua`: PASS for both editions. Create/open/rename/delete folders, move shortcuts, manual/A-Z ordering, reopen, temporarily unavailable mods, separate playthroughs, reset, failed reads/writes, disabling and long-folder scrolling. Reordering now also tests uncommitted movement previews, B cancellation, Start cancellation, folder pickup, failed placement and successful retry.
- `tests/host_integration.lua`: PASS separately for FireRed and LeafGreen. Loads the mod through the real host SDK and sandbox, drives actual HUD input and the native naming keyboard, saves through actual Storage and SaveSerializer, reloads the entire mod runtime, and checks the restored order and folder actions. Verifies that the original shortcut callback receives the correct game/session. No naming or storage facades are replaced in this test.
- The 0.2.1 individual ZIP and manual-install bundle contain byte-identical copies of the tested manifest and all three Lua runtime modules. Individual ZIP checksum matches `docs/releases.json`.

The host integration harness uses imported assets for reads, the host's headless graphics implementation, and an isolated in-memory filesystem for all mod persistence. It does not read or modify player saves. This validates engine integration, not live gameplay or physical-device input/touch.

## Reproduce

From the mod source directory:

```sh
luajit tests/runtime.lua /absolute/path/to/gen1recomp
luajit tests/organizer.lua /absolute/path/to/gen1recomp
```

From the host checkout, for each edition and its imported cache:

```sh
luajit /absolute/path/to/mod/tests/host_integration.lua \
  /absolute/path/to/mod firered /absolute/path/to/firered/data/generated/gba
luajit /absolute/path/to/mod/tests/host_integration.lua \
  /absolute/path/to/mod leafgreen /absolute/path/to/leafgreen/data/generated/gba
```

## 0.2.2 companion suppression

Renderer regression tests passed, including zero native rows or scrollbar rectangles while the companion owns Start, and immediate restoration when ownership ends.
