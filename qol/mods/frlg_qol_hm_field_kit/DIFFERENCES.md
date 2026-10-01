# Differences from vanilla

Use owned HMs with any non-egg party Pokémon, even if its species cannot learn the move. The HM must be in your bag; badge and terrain requirements remain. Moves and PP are never changed.

START > QOL > HM FIELD KIT lists actions currently usable. Existing overworld Cut/Surf/Strength/Rock Smash/Waterfall checks use the same owned-HM fallback. Badge and terrain checks remain. Fly is not added to this menu: use the native Party menu or Dual Screen FLY tile for Fly destination selection. No moveslots are modified; using a field move retains its normal game effects.

## Flash and cave lighting (0.2.0)

Use START > QOL > HM FIELD KIT > FLASH in a dark cave with HM05, the edition’s Flash badge and any non-egg party Pokémon. Flash no longer fails because of missing cave context in older engines. Normal badge and already-used checks remain.

In the mod manager options, toggle **FULL CAVE LIGHTING** to fully illuminate dark caves. Default: off. No HM, badge or compatible Pokémon is required for this display option. Turning it off (or disabling the mod) restores the current native darkness immediately. It does not change save data or Flash flags; using Flash normally still takes effect.

## Native field menu and rods (0.2.1)

Cut, Flash and Waterfall now receive complete native context and run through the native Party action flow. Fish lists owned rods and invokes native Bag Use. No moves are taught or progression flags granted. Dual Screen 0.3.19 respects this kit's enabled setting across field shortcuts.

## Sweet Scent (0.2.4)

On engine 0.3.42+, any non-egg party Pokémon can supply Sweet Scent without learning it. Field Kit and the existing Dual Screen shortcut use native encounters and animations; moves and PP are unchanged. Encounter terrain is required, older engines are gated, and disabling the kit restores learned-move requirements. Sweet Scent has no HM item or badge gate.
