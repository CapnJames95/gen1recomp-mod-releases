# Collection verification

Current package checks pass for **8 installable ZIPs plus the manual bundle and 285 PNGs**, with no broken local links. The suite accounts for all 32 canonical components; only the eight main package archives are distributed. Key Item Wheel, PC Box Tools, Battle Type Hints and Move Inspector are excluded.

Archive CRCs, safe member paths, root manifests/entry points, version/hash metadata, runtime **and Markdown** source identity, galleries and PNG decoding pass. The screenshot audit checks all 285 image hashes and identifies 171 refreshed native previews versus 114 historical examples. No macOS metadata is included.

## Current integration checks

The latest full collection/touch checks pass **4,367 assertions in FireRed, 4,367 in LeafGreen and 4,233 in Emerald**, on both gen1recomp 0.3.39 and 0.3.42. They cover shared Home migration, the Back footer, Emerald navigation routing/black upper viewport and removal of resize/move controls. The preceding documentation audit captured component-manager/schema renders, suite menus/shortcuts, Hoenn panels, starter menus and QoL effects. This follow-up reran the Dual Screen GPU previews and checked the retained gallery against source and its image audit. It changes no shipped gameplay code.

Mac and Thor QoL Test have Gen3DualScreen 0.4.14 with Suite 0.3.9. Sweet Scent requires engine 0.3.42+. Prior installation readback verified 275 mod files per device and preserved saves/settings. Complete gameplay and new hardware screenshot passes remain deferred.

## Sweet Scent follow-up on 0.3.42

[All three isolated Safe Mode retests pass](SWEET-SCENT-RETEST.md): native Party Sweet Scent starts an encounter with zero mods. The same collection/touch counts above also pass on 0.3.42. Six additional native integration runs cover untaught Sweet Scent through the kit and companion tile, including move/PP preservation and guards. This does not establish a complete gameplay pass.

## Retained development evidence

The original development reports remain with their mods. These suites were not all rerun for publication:

- LegalMon 0.17.0 reports 44,126 automated checks and 19,203 independent encrypted PKHeX exports passing.
- The QoL compatibility report records 52 suites, eight Ball Shortcut composition runs and 16 Dual Screen suites passing; see [FIXES.md](../qol/FIXES.md).
- Pokémon Services records 398 checks across both editions, including the Dual Screen launch path.
- Quick Heal Party and Capture Assistant record 140 shared checks per edition.
- Day Care Viewer, Dual Screen and the other mods retain their version-specific validation reports.

Dual Screen device testing is limited to AYN Thor, as confirmed by the maintainer; no other dual-screen devices have been tested. The automated verification does not certify a complete gameplay run of all current mods together. Native-rendered screenshots use fixture state; see [screenshot provenance](SCREENSHOTS.md). Older screenshots may omit new controls or entries.

## Manual-install bundle

The bundle contains `INSTALL.txt` and 8 mod folders (the suite plus seven other packages) under `mods/<mod-id>/`. It uses classic ZIP, uncompressed STORE entries, portable metadata and no ZIP64. Archive contents are checked against the individual packages. All packaged files match their individual releases byte-for-byte; the withdrawn mods are absent.

Rebuild with `python3 tools/build-manual-bundle.py`; verify with `python3 tools/build-manual-bundle.py --check` or `python3 tools/verify-collection.py`. This is for manual extraction, not the launcher's one-mod ZIP import. The previous damaged-download report was not reproduced; this extraction check does not establish its cause.
