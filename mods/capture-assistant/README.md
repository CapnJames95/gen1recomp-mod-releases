# Capture Assistant 0.1.1 — FireRed / LeafGreen

**Press R at the main wild battle command menu** to compare owned balls, inspect capture estimates and read moveset risks. **START → CAPTURE HELP** explains the controls outside battle.

Uses the same native FRLG fonts, blue header, striped background, six-row scrolling menus and player-selected window frames as the other collection tools. Independently installable.

## Install and use

Import [capture-assistant-0.1.1.zip](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.2.0/capture-assistant-0.1.1.zip) through **MODS → Import mod .zip**, enable it and restart.

1. Reach **FIGHT / BAG / POKEMON / RUN** in an ordinary wild single battle.
2. Press the **R shoulder button**, using its current controller/keyboard binding.
3. Choose **Compare owned balls** for current one-throw estimates and stock counts.
4. Open a ball for comparisons at 1 HP and at 1 HP while asleep.
5. Read **Capture risks / moveset**, then return to the battle to choose your own action.

Up/Down scrolls; Left/Right skips five rows; A opens; B/L goes back. R or START closes from any assistant page. Battle processing pauses while the assistant is open. Opening, browsing and closing consume no ball, battle turn or RNG draw. SELECT remains available to Battle Ball Shortcut; START retains its native battle behaviour when the assistant is closed.

## Dual Screen

With **FRLG Dual Screen 0.3.12 or newer** active and displaying its companion screen, pressing R opens Capture Assistant **on the bottom screen over the Dual Screen interface**. The top screen keeps showing the battle. Tap visible rows to open them and **< BACK** to go back or close; physical controls also work. Closing restores the normal companion content.

The battle remains paused while reading. If the companion is disabled or its display is unavailable, the assistant falls back to the normal game screen. Update both packages for this handoff; older Dual Screen releases retain the standalone display.

![Capture Assistant on the bottom screen](../../docs/screenshots/capture-assistant/dual-screen.png)

## Estimates and risks

The list sorts by highest current capture chance, placing Master Balls last. The recommendation excludes Master Balls; ties use item ID, not price. Safari Balls are excluded. No balls means no recommendation.

Calculations call the engine's own catch-odds and ball-bonus functions, then apply its four shake-check thresholds. Current HP, status, terrain, turn count, species catch rate and caught history feed those native functions. These describe the tested engine's rules, not an independent claim of cartridge fidelity. A detected `catch.rate` hook marks the results **baseline only** because another mod can override the actual outcome.

The 1 HP and sleep comparisons are hypothetical. They do not predict damage, turn order, status immunity or whether you can safely achieve that setup. The assistant does not throw balls, attack, inflict status or guarantee a successful strategy.

Risk notes cover roaming, poison/burn, confusion, active weather and selected moves including Teleport, Roar/Whirlwind, Self-Destruct/Explosion, recoil attacks, Curse, Perish Song and Memento. These **inspect the current enemy moveset, including unrevealed moves**. They are possible risks rather than predictions; abilities, move failure and other mechanics may prevent them. Residual effects and capture hazards are not exhaustively modelled.

Trainer, Safari, double, linked, spectator, tutorial and ghost battles are excluded. Incompatible command states do not open the assistant. A native modal layer reserves input ownership. Dual Screen also provides a Home tile for the field help screen; battle estimates open with R during a supported encounter.

## Compatibility and validation

Mod API 2, FRLG only, `engine_internals`. Tested with upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. The declared engine range does not verify every intervening release. Other mods owning R or replacing battle UI/update methods may conflict. No imported game data or save files are shipped.

See [VALIDATION.md](VALIDATION.md). Automated native-data, loader, calculation, ownership and control checks pass in both editions; physical controller/Android device testing remains outstanding.

## Screenshots

Native font/frame drawing traces from synthetic test sessions, not live-play captures.

![Capture Assistant home](../../docs/screenshots/capture-assistant/capture-home.png)

![Owned ball comparison](../../docs/screenshots/capture-assistant/capture-balls.png)

![Ball detail and hypothetical improvements](../../docs/screenshots/capture-assistant/capture-detail.png)

![Capture risk notes](../../docs/screenshots/capture-assistant/capture-risks.png)

Based on the Pokemon Gen 1 Recompilation Project by BOIS CLUB GAMES, LLC. Menu styling follows the collection's Day Care Viewer and LegalMon conventions.
