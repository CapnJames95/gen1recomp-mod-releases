# Auto Surf 0.2.0

Press A facing adjacent water to start Surf directly. Walking into water does nothing extra.

Experimental FRLG beta mod for players. Tested against upstream commit `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf` with ROM-free fixtures; not device-playtested.

## Install

Import this ZIP with launcher MODS > Import mod .zip, enable and restart. Alternatively put this folder at `mods/frlg_qol_auto_surf/`. Independently installable; no shared package needed. Back up your save for beta testing. Restart after installing, disabling or updating; restart fully after a load error.

## Use and configuration

Stand next to water, face it, then press the game's **A** button (including its mapped controller/keyboard button). This skips the YES/NO prompt and the “used Surf” text and starts the normal Surf animation/execution. Walking or holding a direction does not trigger it. Requires the normal badge and party Surf capability (or HM Field Kit). NPCs, signs, hidden items and map scripts retain native interaction priority. Does not bypass movement, UI or script locks. While biking, the native interaction is left unchanged.

Disable ENABLED to restore the game's normal A-button confirmation. The existing mod ID is unchanged: replace the old Auto Surf Prompt package, do not install a second copy, and restart the game.

ENABLED and any other settings live in this mod's manager entry. Tools share one START > QOL menu automatically.

## Compatibility and validation

FireRed and LeafGreen only. Uses declared `engine_internals`; later beta changes or other mods replacing the same functions may conflict. Inactive wrappers fall through after a loader change. Online/arena play excluded. See VALIDATION.md for test results; upstream modkit lint/validate can check this folder. No ROM data or extracted assets included.

## Screenshots

Native FRLG mod-manager renders from the loaded 0.1.0 package in an isolated test session. These show the real detail/options UI; they are not live gameplay captures.

![Auto Surf Prompt details](../../../docs/screenshots/frlg_qol_auto_surf-detail.png)

![Auto Surf Prompt options](../../../docs/screenshots/frlg_qol_auto_surf-options.png)

## Compatibility update (0.1.1)

Shared Start-menu rendering yields to the dedicated Scrollable Start Menu when enabled. Independently installable; restart after replacement.
