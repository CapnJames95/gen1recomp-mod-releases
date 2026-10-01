> **Historical development record.** Version counts, compatibility and pending-work statements below describe the original FRLG work. Current three-game scope is in the [suite README](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/mods/frlg-qol-suite/README.md) and [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).

Current release status: see [FIXES.md](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/qol/FIXES.md) for the September 27 cleanup, fixes and new validation. Older validation/checklist entries below are historical.

Current update: 24 core packages; PC Box Tools removed; Quiet EXP added; Battle Hints and Move Inspector removed. Ball, shop and Start integration fixed; controller hold added. Historical scope checklist follows.

# Complete request checklist

“Implemented” means source and an independent installable package with automated checks, not interactive gameplay certification. “Native” means already present in the inspected official revision. Partial items state their limits rather than claiming full coverage.

| Requested idea | Result |
| --- | --- |
| Run indoors | Native: Player.canDash gates Running Shoes, not indoor maps. No redundant package. |
| Running from start | running_start: B-dash without changing story flags. |
| Fast/instant text | instant_text: dialogue page reveal; retains choices and confirmations. Not every custom animation's embedded text timer. |
| Reusable TMs | reusable_tms: successful immediate/deferred teaching retains TM; ordinary removal unaffected. |
| HMs without moveslots | hm_field_kit: owned HM, compatible non-egg party member; native badge/terrain checks. Menu and overworld actions share fallback. Fly destination UI is not provided: WorldAPI.flyTo is unsupported. Native party Fly still needs a taught move to appear. |
| Move reminder from party | party_reminder: START; native FRLG cost of two Tiny Mushrooms or one Big Mushroom, success-only payment. |
| Nickname from party | party_nickname: SELECT; eggs/traded Pokemon restrictions preserved; native naming screen. |
| Battle Ball shortcut | ball_shortcut: configured Poke/Great/Ultra Ball in ordinary wild singles. Excludes tutorials, ghosts, Safari, doubles, link and spectators. Native battle consumes the Ball. Last-used tracking is not included. |
| Repel reuse prompt | repel_reuse: after native expiry message; default No; prefers last-used available Repel then stocked fallback. |
| Automatic berry replacement | berry_restock: actual battle-consumed berry only, one from Bag, after writeback to the same party Pokemon. No free berries or restoration of merely stolen/knocked-off items. |
| Faster Center healing | fast_healing: 2×/4×/8× animation; no idle jingle wait by default. Audio finishes in the background; optional original wait, native healing/callbacks and dialogue remain. |
| Faster saving | quick_save_prompt removes redundant second confirmation only. Actual native serialization/write/error handling remains; no unsafe asynchronous save patch. |
| Faster PC/box transitions | Switching boxes is already immediate. Entry/exit animations remain native; no extra save prompts added. |
| Improved PC controls | PC Box Tools removed at user request; native PC and Dual Screen behavior are unchanged. |
| Bag sorting | bag_sort: displayed pocket rows by name, quantity or item ID; saved inventory order unchanged. TM Case/Berry Pouch submenus remain native. |
| Auto-pocket new items | Native Bag.add routes items into their proper pockets. |
| Summary nature/ability/IV/EV info | summary_info: nature effects and ability; optional IV/EV display off by default. Native ability description retained. |
| Improved move information/display | move_info: native type/category, power, accuracy, current/max PP and descriptions, paged from Summary. Not a replacement battle HUD. |
| Optional battle effectiveness/STAB | battle_hints: hold SELECT in single-battle move menu. Type-chart effectiveness and STAB only; excludes abilities, weather, items and other damage modifiers. |
| Pokedex search | dex_companion: literal name search and seen/owned list; optional unseen spoilers. Uses imported species IDs rather than assuming National Dex numbers match. |
| Pokedex locations/evolutions | dex_companion: imported wild-area and evolution records; method labels/parameters, not a comprehensive human-language walkthrough. |
| Route completion | dex_companion: unique ordinary encounter species for current map, owned count. Static/gift/event species, custom encounter hooks, time/story availability and encounter odds not modeled. |
| Granular battle speed | battle_pacing: independent HP/EXP instant bars using native tween paths. Native overall battle speed and animation toggle remain. No arbitrary animation-script time scaling. |
| Hold-to-fast-forward | hold_fast_forward: temporary configurable key/factor, respects engine speed locks and does not rewrite saved speed. No additional gamepad hold binding. |
| Controller remapping / keyboard QoL | Native Input applies saved keyboard/gamepad bindings; engine owns input mapping. No replacement FRLG binding-editor screen shipped. Existing bindings control logical shortcut buttons. Keyboard hold-speed added separately. |
| Separate audio controls | Native FRLG MUSIC VOL and SFX VOL; no duplicate controls mod. |
| Configurable speed-up | Native overworld/battle/menu speeds; temporary hold-speed package supplements them. |
| Central QoL toggles | Per-mod manager settings plus a shared tool-menu entry only where useful; no dependency. |
| Auto-bike Cycling Road | Native scripted ForcePlayerOntoBike behavior and resume-after-Surf handling. Not a separate no-op mod. |
| Auto Surf | auto_surf: press A facing water to start native Surf without confirmation/used-Surf text; walking does not trigger it. Normal prerequisites and interaction priorities remain. |
| Remember battle move | Native within-battle active-mon cursor memory. Persistence across different battles is not added. |
| Remember Bag pocket | Native per-pocket cursor/scroll and remembered pocket. Sorting affects displayed ordering, not this native mechanism. |
| VS Seeker readiness | vs_seeker_status: dynamic battery/readiness in Bag description, no always-on HUD. |
| Town Map service/Fly information | map_services: SELECT service notes for main towns and native Fly-map eligibility at cursor. Read-only, not destination unlocking or a new Fly implementation; services may be story-gated. |
| Shop owned count | shop_count: count while browsing, supplements native quantity-dialog count. |
| Party held-item display | party_items: L read-only party item-name panel; native icons remain. |
| Evolution “not now” | Native B cancellation during cancellable evolution. No added pre-evolution scheduling prompt, stone/trade bypass or permanent “never evolve” state. |
| Improved key-item acquisition descriptions | key_item_help: nine authored item explanations, safe deferred first-acquisition popup through Bag.add, Bag descriptions. Unknown items/direct inventory writes retain native behavior. |
| Widescreen/resolution/window/save slots/screenshots | Engine-owned; see ENGINE_FEATURES.md. No engine patch shipped. |

## Current beta limitations

The public mod surface does not expose every needed FRLG interaction. These packages declare engine_internals and wrap the actual FRLG modules; generic Gen 1 hooks alone are not sufficient. Target commit pinning, loader lifecycle gates and restart instructions mitigate—not eliminate—private-API fragility.

Unsupported Fly destination API, lack of a unified safe animation-timing API, and lack of a complete encounter/availability model constrain the partial features above. Several other omissions are deliberate scope/safety choices, **not claims that they are impossible to implement**.
