# Quick Field Actions 0.3.0

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Press A facing a field obstacle to use Surf, Cut, Strength, Rock Smash or Waterfall directly. Walking into an obstacle does not trigger this feature.

Experimental FRLG beta mod for players. Tested against upstream commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf` with ROM-free fixtures; not device-playtested.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

## Use and configuration

Face the correct target and press the game's **A** button (including its mapped controller/keyboard button):

| Move | Target / effect |
| --- | --- |
| Surf | Adjacent water: start surfing. |
| Cut | A cuttable tree: remove it. |
| Strength | A pushable boulder: activate Strength, then push by walking. |
| Rock Smash | A smashable rock: break it using the normal field action, including any native encounter. |
| Waterfall | While surfing, face up into a waterfall: start climbing. |

Skips the YES/NO prompt and used-move text. Normal animations, effects, badge requirements and party move capability remain in place. HM Field Kit can provide capability under its own settings. NPCs, signs, hidden items and map scripts retain native interaction priority; movement, UI and script locks are respected. While biking, the native interaction is left unchanged. Cut grass, other field moves and party-menu actions are unchanged.

Disable ENABLED to restore native confirmations. **Renamed from Auto Surf**, with four new field actions in 0.3.0. The internal ID `frlg_qol_auto_surf` and saved setting remain unchanged, so existing suite settings carry over. Update the suite and restart.

ENABLED and other settings live in START → QOL → QOL SETTINGS. Tools share one START > QOL menu automatically.

## Compatibility and validation

FireRed, LeafGreen and Emerald through the current QoL Suite on gen1recomp 0.3.39. Uses declared `engine_internals`; later beta changes or other mods replacing the same functions may conflict. Inactive wrappers fall through after a loader change. Online/arena play excluded. See VALIDATION.md for test results; upstream modkit lint/validate can check this folder. No ROM data or extracted assets included.

## Screenshots

Current component-manager previews rendered from this source in an isolated FireRed test session. These are component configuration examples; install the combined suite. These show the real detail/options UI; they are not live gameplay captures.

![Quick Field Actions details](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_auto_surf-detail.png)

![Quick Field Actions options](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/frlg_qol_auto_surf-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Update the QoL Suite and restart.
