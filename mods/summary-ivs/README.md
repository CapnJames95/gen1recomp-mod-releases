# Summary IVs 0.2.4 — Emerald / FireRed / LeafGreen

**Emerald (QoL Suite 0.3.2):** the Skills page now shows a six-stat **IV/EV table immediately**, for owned Pokémon and the read-only wild inspector. **A** toggles native calculated stats; **B** first returns to native stats, then closes normally. Page and Pokémon navigation remain available. Gen3DualScreen 0.4.4 renders the same panel during wild battles. FR/LG retains its inline IV column.

**Suite component source:** This feature is now distributed only in [FRLG QoL Suite](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md). Import the suite, then use **START → QOL → QOL SETTINGS** to toggle it or edit its options. Disable any older standalone installation and restart. This folder is retained for rebuilding and testing, not as a separate release.

Adds **IV 0–31** beside HP, Attack, Defense, Sp. Atk, Sp. Def and Speed on the native **Pokémon Skills** summary page, in the orange gap between the labels and stat totals. Uses the game's small font and normal text colours, matching native FRLG/LegalMon styling. The original right-hand numbers are calculated stats, not EVs; they remain unchanged.

Historical preview (older build): [IVs beside the native stat labels](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/screenshots/summary-ivs/firered.png).

## Install and configuration

Import the QoL Suite and enable this feature in **START → QOL → QOL SETTINGS**. Disable any older standalone copy and restart.

Open a Pokémon's Summary and switch to **Pokémon Skills**. No extra button or submenu is needed. **SHOW IVS** in this mod's settings turns the mod on/off; it defaults to on. Works for party and PC summaries using the native renderer. Eggs and unrelated enemy summaries are excluded. Missing/invalid IV data displays `--`, never a guessed zero. The column hides during page animations and refreshes when changing Pokémon.

## Inspect an uncaught wild Pokémon

Press keyboard **I** or controller **X / West** at the ordinary wild-battle **FIGHT / BAG / POKéMON / RUN** menu. There are no persistent buttons, HUD additions or automatic pop-ups. No caught/seen requirement applies. This uses exactly the native Pokémon Summary renderer used by the PC, not a separate custom inspector design.

The native summary opens on **POKéMON PREVIEW** (the Skills layout): all six IVs and calculated stats, HP, nature and ability. The top-right blue area displays the same nature name as Pokémon Info instead of the D-pad/PAGE hint. The title changes only in this wild inspector; party and PC Skills titles remain unchanged. Left/right changes native pages for species, typing, gender/shiny presentation, held item, experience, moves, PP, power, accuracy and descriptions. **Select toggles IV/EV values** on Preview. **B** backs out of move details, then closes the summary; pressing the configured inspector hotkey again also closes it. The battle pauses while inspecting; closing does not select a battle action. All Pokémon data is a detached snapshot, with move reordering disabled. Reopen to refresh it.

**INSPECT KEY** is now a text setting: select it in QOL → QOL SHORTCUTS → WILD INSPECTOR and enter a single LÖVE keyboard key name. Examples: `k`, `space`, `tab`, `return`, `escape`, `f1`–`f24`, `lctrl`, `rshift`, `kp1` or `;`. Names are case-insensitive and surrounding whitespace is ignored. `enter`, `esc`, `ctrl`, `shift`, `alt` and `cmd` are accepted aliases (unqualified modifiers mean the left key). Enter `off` to disable; I is the default. Existing saved bindings are preserved when upgrading; set INSPECT KEY to `i` and INSPECT BUTTON to X / West or reset this mod’s settings to adopt the new default. This is a key-name entry field, not a press-to-record dialog; multi-key chords and mouse buttons are not supported.

**INSPECT BUTTON** defaults to X / West and now offers every standard SDL gamepad button: A/B/X/Y, both shoulders, both stick clicks, all four D-pad directions, Back/Share, Start/Menu and Guide/Home, plus LT/L2 and RT/R2 triggers, or OFF. Triggers fire once above 60% travel and rearm below 30%; holding or jittering does not repeatedly toggle the preview. Existing controller settings are preserved. Raw numbered joystick buttons and stick-axis directions are not exposed as bindable buttons by this mod.

**WILD INSPECTOR** disables just this feature. If you customize bindings, choose inputs not already used by another action or mod. OS-reserved shortcuts and Guide/Home may not reach the game. Outside a supported encounter, input passes through unchanged.

Supported: ordinary single wild battles, including Pokémon never caught. Trainer, link/online, spectator, double, Safari, tutorial and unidentified ghost battles are deliberately excluded. Cannot open during animations, queued actions, another menu or Help. Stat totals are native summary values, not damage predictions or stage-adjusted battle stats; temporary transformation/type changes are not a separate live battle report. Native OT/met fields for an uncaught Pokémon are encounter placeholders, not final capture ownership/history. Missing values are not inferred.

This is read-only: no stat recalculation, EV/IV editing, save changes or encounter RNG draws. The inspector hotkey is consumed only when inspection can open or close. Expanded Summary Info can remain enabled for its separate nature/EV details menu; neither mod requires the other.

## Dual Screen

Use **Gen3DualScreen 0.3.13 or newer**. With this mod enabled, its Skills page uses the native orange summary on the companion screen rather than Dual Screen's custom stat panel. Physical controls navigate it; the native fallback does not add touch hit targets. Disabling SHOW IVS restores the companion adapter. Older Dual Screen versions replace this page and do not show the inline column; update Dual Screen or disable it.

## Compatibility and validation

API 2, `engine_internals`, FireRed and LeafGreen beta. Tested against upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`; other engine versions or third-party summary replacements may need adaptation. No ROMs, extracted textures, fonts or player saves are included in the mod.

188 native-data checks pass per edition (376 total), including all six mappings, zero/31, invalid data, PC selection, toggle/reload/unload, session changes, animation guards and unchanged native text/stat positions. Inspector checks cover keyboard/controller activation, repeat suppression, native summary navigation, EV switching and width, scoped Preview title/nature hint, read-only snapshots, move-swap prevention, battle pausing, close-button isolation, excluded battle types and stale sessions. Native render traces were rendered and visually inspected. Physical-device gameplay has not been tested for this addition.

Reproduce from the engine checkout:

```sh
LUA_PATH='./?.lua;./?/init.lua;;' luajit /path/to/collection/tools/summary-ivs/test.lua /path/to/collection firered /path/to/firered/data/generated/gba
```

Repeat with `leafgreen` and its imported cache. Tests use synthetic Pokémon, never your saves.
