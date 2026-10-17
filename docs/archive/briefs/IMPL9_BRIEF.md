# Implementer task impl9 — main menu, sound effects, effect manager

Read `specs/IMPL_TEMPLATE.md` first and follow it. Then docs (README → STATUS → DECISIONS → FORMATS) and the specs
below. Deliverables (ONLY these three; finish and verify one before the next):

1. Main menu — `specs/opus/12_menus_hud.md` §1–2: boot logo/loading, top menu, difficulty select, character/team
   select, practice stage select, option screen (wire the fields to an in-memory config; saving th08.cfg is a later
   task), replay/music room/spell practice as stubs that return to the menu. Replace the title stub so the whole game
   is reachable from the menu with the keyboard (and on the web).
2. Sound effects — `specs/opus/13_sfx_effects.md` §1 (+ 10 §10): SE table, load the wavs from th08.dat, per-frame
   queue with dedup/pan averaging and the volume curve, mix through the existing cpal audio path (web too); hook every
   call site listed in the spec (shots, graze, items, extend, death, bomb, enemy damage/death, ECL bullet sounds,
   menu cursor/select/cancel, spell card, timeout tick).
3. Effect manager — `specs/opus/13_sfx_effects.md` §2–3: entries/ring cursor, the 66 types, every spawn site
   (hit sparks, enemy death bursts, player death rings, item/bonus text, spell backgrounds), ScreenEffect types 0–7
   (shake/flash/fade), the ring renderer, draw lists/layers.

Verify with screenshots (menus, enemy death bursts, player death ring, spell background, screen shake) and by checking
the SE queue in a log/test. Keep the wasm check passing. Bomb choreography from spec 14 is a later task.
