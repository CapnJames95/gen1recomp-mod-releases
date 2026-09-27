# Collection verification

Current publication checks passed for **38 individual ZIPs, 248 matching runtime files, 174 PNGs and 38 mod galleries**, with no broken local links. All 38 overview links point to their full README sections. There are ten main downloads and 28 QoL packages, plus the manual-install bundle. Four-Item Wheel and PC Box Tools are excluded.

Every current source mod has exactly one individual package. Archive CRCs, safe member paths, root manifests/entry points, version/hash metadata, runtime/source identity, galleries and PNG decoding pass. No macOS metadata is included. The verifier excludes unrelated local `outputs/` task artifacts from published documentation/archive checks.

## Current integration checks

All current mods loaded together in both editions. Dual Screen collection integration passed **362/362 checks per edition** with synthetic sessions. These checks do not use player saves or establish physical-device behaviour. Dual Screen's device-testing scope remains **AYN Thor only**; other dual-screen devices are untested.

## Retained development evidence

The original development reports remain with their mods. These suites were not all rerun for publication:

- LegalMon 0.17.0 reports 44,126 automated checks and 19,203 independent encrypted PKHeX exports passing.
- The QoL compatibility report records 52 suites, eight Ball Shortcut composition runs and 16 Dual Screen suites passing; see [FIXES.md](../qol/FIXES.md).
- Pokémon Services records 398 checks across both editions, including the Dual Screen launch path.
- Quick Heal Party and Capture Assistant record 140 shared checks per edition.
- Day Care Viewer, Dual Screen and the other mods retain their version-specific validation reports.

Dual Screen device testing is limited to AYN Thor, as confirmed by the maintainer; no other dual-screen devices have been tested. The automated verification does not certify a complete gameplay run of all current mods together. Native-rendered screenshots use fixture state; see [screenshot provenance](SCREENSHOTS.md). Older screenshots may omit new controls or entries.

## Manual-install bundle

The bundle contains `INSTALL.txt` and all 38 mod folders under `mods/<mod-id>/`. It uses classic ZIP, uncompressed STORE entries, portable metadata and no ZIP64. macOS `ditto` extracted it successfully, and every extracted file matched the archive. All packaged files match their individual releases byte-for-byte; the withdrawn mods are absent.

Rebuild with `python3 tools/build-manual-bundle.py`; verify with `python3 tools/build-manual-bundle.py --check` or `python3 tools/verify-collection.py`. This is for manual extraction, not the launcher's one-mod ZIP import. The previous damaged-download report was not reproduced; this extraction check does not establish its cause.
