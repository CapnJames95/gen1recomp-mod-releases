> **Historical development record.** Version counts, compatibility and pending-work statements below describe the original FRLG work. Current three-game scope is in the [suite README](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md) and [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).

# Engine-owned features

Target: official dev commit `84e076b2d1e2dda36073ff55ec7c311a6b97519c`.

No engine patches are included. These behaviors either already exist or require coordinated engine work rather than a loadable gameplay mod.

| Feature | Ownership / reason |
| --- | --- |
| Native widescreen gameplay | Requires coordinated viewport, map culling, camera, battle/UI layout and input-coordinate changes. Stretching a 240×160 canvas is not native widescreen. A mod overlay cannot safely supply all of this. |
| Resolution / window modes / fullscreen | Engine video/output handling: src/core/VideoMode.lua, src/core/FaithfulRes.lua, renderer and FRLG option rows. Do not override the window lifecycle in gameplay mods. |
| Save slots | Engine persistence/launcher metadata and migration. Gameplay mods should not invent competing slot paths or write raw saves. |
| Screenshots | Engine main.lua already calls love.graphics.captureScreenshot. No ROM-bearing screenshot asset is bundled. |
| Input remapping | src/core/Input.lua applies binding overlays; Game3:applyOptions honors them. The shared BindingsMenu is engine UI; the FRLG option rows do not themselves supply a full rebinding screen. No claim is made that a new in-game FRLG remapping panel was implemented here. |
| Separate audio levels | src/ui/game3/option_rows.lua contains MUSIC VOL and SFX VOL, applied through FRLG audio. Already native. |
| Speed configuration | Existing overworld, battle and menu speeds plus native speed-lock restrictions. Hold Fast Forward respects rather than replaces these. |
| Fast save I/O | SaveMenu calls the native write pipeline. This is not GBA flash emulation with an arbitrary removable “saving a lot of data” sleep. The package reduces redundant confirmation, not disk durability or error checks. |
| Further timing changes | Battle move scripts, sounds, scene fades and callbacks are coupled. No supported general-purpose FRLG animation multiplier was found. HP/EXP bars use the existing instant path; healing speeds only its dedicated machine step. |

## Already-native QoL

- Indoor running: src/core/game3/player.lua, Player.canDash.
- Cycling Road bike enforcement: src/core/game3/scripting/natives_events.lua, ForcePlayerOntoBike.
- Bag pocket/position memory: src/ui/game3/bag_menu.lua.
- Active battler's remembered move cursor: src/core/game3/battle/ui.lua, open_move_menu. This is not persistence between battles.
- Evolution cancellation: src/ui/game3/evolution_scene.lua, handleInput. Only during the native cancellable window and when _canStop is true.
- Current box and immediate box changes: storage and box_storage_ui modules.

These observations come from source inspection of the pinned revision, not a claim that every engine feature has been exercised interactively.
