# Implementer task impl8 — dialogue, game manager flow, HUD

Read `specs/IMPL_TEMPLATE.md` first and follow it. Then docs (README → STATUS → DECISIONS → FORMATS) and the specs
below. Deliverables (ONLY these three; finish and verify one before the next):

1. Dialogue — `specs/opus/10_msg.md`: msg*.dat loader + interpreter (all 23 opcodes), portraits/face ANMs, text box
   and text rendering (draw the text with a bundled-free approach: render glyphs on CPU into a texture; any reasonable
   font rasterisation is fine, mark SPEC-GAP for exact GDI pixels), skip rules, ECL/timeline interaction
   (ops 148/158/179–181, timeline ops 6/7, what Msg_IsActive blocks), BGM change hooks, stage end (op 9).
2. Game manager — `specs/opus/11_rng_and_flow.md` §2–5: GM object + stats block, new game / stage start defaults per
   difficulty and mode, GameMgr_Calc per-frame flow, stage routing (4A/4B, 6A/6B, Final A/B), death / game over /
   continue (continue menu from 12 §4), pause (12 §3 pause menu), rank → ECL rank var, extends. Wire the stage scene so
   a full run 1 → 6 → ending-stub works with `TH08_INPUT` scripts and with the keyboard.
3. HUD — `specs/opus/12_menus_hud.md` §5: front.anm panel (score, hiscore, lives, bombs, power, graze, point, time,
   gauge), boss UI (life bar, spell name/bonus, timer), popups, stage-clear panel, stage title.

Verify with screenshots (dialogue on stage 1 boss, HUD during play, pause menu, continue menu, stage clear panel,
stage 4 route choice) and unit tests for flow/routing. Keep the wasm check passing.
Do NOT implement the main menu, sound effects, replays or score.dat here (later tasks).
