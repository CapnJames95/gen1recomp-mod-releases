# Quick Heal Party 0.1.0 — FireRed / LeafGreen

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

**START → QUICK HEAL** — preview and apply healing items from your Bag to the whole party or one Pokémon.

Uses the collection's native FRLG fonts, blue header, striped background, six-row scrolling menus and the player's chosen window frame. Independently installable; no other mod is required.

## Install and use

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

1. Open **START → QUICK HEAL**.
2. Choose **Preview healing: whole party** or **Heal one Pokemon**.
3. Open **Items to spend** and **Preview party results** to inspect the proposed changes.
4. Choose **Confirm: use … item(s)**. The initial selection is Cancel.
5. Save normally to retain the changes.

Up/Down scrolls; Left/Right skips five rows; A chooses; B/L goes back; START closes. The native menus pause the field. Dual Screen may display these through its native menu fallback; dedicated Home tiles and direct touch rows are not included.

## Healing preferences

- **Use premium medicine: OFF** by default. Preserves Full Restores, Max Potions and Max Revives. Turn it on to make these available to the planner.
- **Revive fainted Pokemon: ON** by default.
- **Cure status conditions: ON** by default.

Preferences can be changed in this menu or in the mod manager; both use the normal options persistence path. The manager also has an ENABLED toggle.

The planner uses Potions, Super/Hyper/Max Potions, Full Restores, ordinary status medicine, Revives/Max Revives and HP-restoring drinks. It skips eggs and never selects berries, bitter herbs, Sacred Ash, PP restorers, PP boosts or Rare Candies. Held items stay held.

Party order receives priority when stock is limited. For HP, it chooses the smallest sufficient available heal, or the largest when nothing is sufficient, repeating as needed. This is a practical heuristic, not a globally optimal purchase-cost or inventory allocation solver. The preview reports Pokémon still needing care when supplies or preferences prevent full treatment.

Previewing uses copies and native item-effect routines. Confirmation rechecks party identity, party state and inventory, then uses normal field item actions and consumption. A changed preview is rejected. If another mod refuses or changes an item effect, the remaining batch stops and reports the interruption; already applied items remain applied.

## Compatibility and validation

Mod API 2, FireRed/LeafGreen/Emerald, `engine_internals`. Tested with upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`. The manifest's version range is not a promise of compatibility with every engine revision. No game data or save files are shipped.

See [VALIDATION.md](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/quick-heal-party/VALIDATION.md). Automated checks use native imported data and synthetic sessions in both editions. Physical device/controller playthrough testing is outstanding.

## Screenshots

Actual native drawing traces with imported fonts and frames, rendered from synthetic test sessions; not live-play screenshots.

Historical preview (older build): [Quick Heal home](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/quick-heal-party/quick-heal-home.png).

Historical preview (older build): [Healing review](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/quick-heal-party/quick-heal-review.png).

Historical preview (older build): [Exact items to spend](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/quick-heal-party/quick-heal-items.png).

Historical preview (older build): [Party result preview](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/quick-heal-party/quick-heal-results.png).

Historical preview (older build): [Healing preferences](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/quick-heal-party/quick-heal-options.png).

Based on the Pokemon Gen 1 Recompilation Project by BOIS CLUB GAMES, LLC. Menu styling follows the collection's Day Care Viewer and LegalMon conventions.
