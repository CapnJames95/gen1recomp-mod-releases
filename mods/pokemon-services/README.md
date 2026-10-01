# Pokemon Services 0.1.3

Current companion preview (synthetic Emerald session; Dual Screen is optional):

![Current pokemon-services menu](https://github.com/CapnJames95/gen1recomp-mod-releases/raw/refs/heads/main/docs/screenshots/current/emerald-pokemon-services.png)


**Emerald support (QoL Suite 0.3.7):** Uses native Hoenn PC/healing, Name Rater, Move Deleter and Move Reminder services. Lilycove has six item counters and rooftop drinks; decorative furniture counters are not included. Two Island's shop is FRLG-only. Emerald daycare is Route 117. The free reminder consumes no Heart Scale; the separate party reminder still uses normal payment. Native scripts, purchases, naming ownership, move deletion/relearning and daycare fees pass automated tests. Remote services are unavailable during active Frontier challenges. Manual device testing remains pending.


**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Native FireRed / LeafGreen services from **START → MODS → Pokemon Services → OPEN SERVICES**, or **START → SERVICES**. Matches the collection's blue headers, native user-selected frames and scrolling controller menus.

## Install

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

With [Gen3DualScreen 0.3.13](https://github.com/CapnJames95/gen1recomp-mod-releases/releases/download/v1.3/frlg-dual-screen-0.4.14.zip), the **SERVICES** Home tile opens the same menu and replaces the duplicate START entry. The Mods-menu action remains available. Earlier companion versions can use the Mods-menu action or START entry.

## Included services

| Service | Native behavior |
| --- | --- |
| Pokemon PC | Original storage menu: withdraw, deposit, move Pokemon and move held items; original storage screens and restrictions. |
| Item PC | Original player PC, including item deposit/withdrawal and mailbox. |
| Heal entire party | The same `Party.healAll` routine used by the engine's `HealPlayerParty` special: HP, PP, fainting and status restoration, free. Confirmation defaults to Cancel. |
| Poke Marts | Original inventories for Viridian, Pewter, Cerulean, Vermilion, Lavender, Fuchsia, Saffron, Cinnabar, Three, Four, Six and Seven Island, Indigo Plateau and Trainer Tower. Native buy/sell screen, prices, quantity choices, money and bag limits. |
| Two Island shop | Original merchant script chooses among all four progression-dependent inventories. |
| Celadon department store | 2F general goods and TMs, 4F evolution stones, 5F vitamins and battle items, plus rooftop vending machines. Fresh Water, Soda Pop and Lemonade use the original vending script and prices. |
| Move Reminder | Free native party selection and move-learning UI. No mushrooms are required or consumed. Native move eligibility, replacement and cancellation rules remain. |
| Move Deleter | Original Fuchsia script and move-selection screen, including HM removal and the last-move restriction. |
| Name Rater | Original Lavender script and naming screen. Native ownership, Egg and name-length restrictions apply. |
| Day Care | Check deposited Pokemon and withdrawal fees, deposit from party and withdraw remotely at Route 5 or Four Island. Uses native deposit, training, move-learning, money and withdrawal routines. |

Remote access bypasses travel to the service, including shops in places you have not visited. It does not unlock map access or unlock the Pokedex. Viridian opens its regular shop inventory directly, without running Oak's Parcel quest. Department-store NPC gifts, tutors and rooftop drink-for-TM exchanges are not shop counters and are not included.

Day Care egg collection remains at Four Island, as in Day Care Viewer. Collect a waiting egg before changing its parents. Day Care screens show a snapshot; use **Refresh** to update it. Deposits and withdrawals recheck the selected Pokemon, space, pending eggs and quoted fee before acting.

**Up/Down** selects, **Left/Right** skips five entries, **A** opens, **B/L** goes back and **START** closes. Native service screens keep their original controls. Leaving a native service returns to the field; reopen Services for another task.

Services run only in an idle field session, outside battles, movement, dialogue, other native menus, Safari games and linked activities. Use the normal **START → SAVE** menu after changes you want to keep; service actions do not auto-save. Disable overlapping automation while managing your party. These are engine-internal integrations; future engine versions can change compatibility.

## Verification

**402 automated checks passed:** 194 native-data checks plus 7 Dual Screen integration checks per edition. Actual imported scripts exercise shop progression, drink purchases, name ownership, HM deletion, free move relearning with no mushrooms, preservation of owned mushrooms, eligibility and cancellation. Native shop transactions, healing, Day Care charges, menu registration and busy-state checks also pass. Modkit lint, validation and Gen III compatibility checks pass. See [VALIDATION.md](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/pokemon-services/VALIDATION.md).

Screenshots below render the actual menu drawing code with isolated fixture state and locally imported fonts. They are not live-play captures. Physical controller and Android playtesting remain outstanding. No ROM assets or player saves are distributed in the ZIP.

| Services | Department store |
| --- | --- |
| Historical preview (older build): [Services](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/pokemon-services/services-home.png). | Historical preview (older build): [Department store](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/pokemon-services/services-department.png). |

| Party healing | Day Care |
| --- | --- |
| Historical preview (older build): [Healing](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/pokemon-services/services-heal.png). | Historical preview (older build): [Day Care](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/pokemon-services/services-daycare.png). |


## Native Pokémon legality corrections — 0.1.1

This release includes the shared FRLG generation/export corrections. It sets valid ability slots for newly generated/caught Pokémon, creates native gift eggs with the correct egg metadata, preserves fixed NPC-trade identity and contest values, and generates new roamers with retail FRLG PID/IV correlations. The roaming beast's stored personality and IVs now reach the battle without being regenerated. Native unhatched eggs receive the required OT-name padding during in-game export.

The same helper is bundled independently with Dual Screen, Shiny Hunter, Encounter Reset, Encounter Tour, Day Care Viewer and Pokémon Services. No additional mod is required. Co-loading these packages applies the corrections once; disabling every participating mod or unloading the game stops the wrappers. Existing Pokémon are not rerolled or bulk-repaired.

**For a cartridge save, use MODS → this mod → SAVE + EXPORT while in the field.** This first saves the active game and then exports with the egg-name correction loaded. The log gives the output path under `exports/<edition>/`. A fresh launcher export can still use the host's unpatched egg-name encoder; copy the in-game export directly. Restart after installing updates.

See the collection's `docs/LEGALITY-FIXES.md` for the regression results and limits. This corrects the identified defects; a passing sample matrix does not certify every possible modified ROM, species combination or future host release.
