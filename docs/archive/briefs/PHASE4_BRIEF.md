# Clean-room brief — Phase 4: dialogue, RNG, game flow

Same role and rules as before (TASK_TEMPLATE.md, RE_WORKFLOW.md). Continue in your SPEC_DIR: re-read NOTES.md
(especially "For later phases" and the items deferred to spec 11), symbols.csv, structs.md and specs 00–09 first.

Behaviour per frame, struct tables, opcode tables, short pseudocode; never paste decompiled code. Mark VERIFIED/INFERRED.

Deliverables (ONLY these three; finish and verify one before the next):
1. `10_msg.md` — dialogue files (msgN*.dat): file layout, script opcodes (all used in data), portrait/face ANM
   handling, text box and text rendering (font, colours, line layout), timing/skip rules, interaction with ECL/timeline
   (ops 148/158/179–181, timeline ops 6/7), boss-name/BGM-change hooks. Tool: dumper with 0 problems on all msg files.
2. `11_rng_and_flow.md` — RNG algorithm, state, seeding (new game / replay / practice); every consumer that matters for
   sync; GameManager: new-game init (lives/bombs/power/score/rank defaults per difficulty and mode), stage start/end,
   stage transitions (4A/4B, 6A/6B routing, Final A/B), boss/spell-card sequence glue, time/night system as far as the
   game state needs, continue, game over, pause; Supervisor scene state machine (all scene ids and transitions); the
   stats block layout.
3. `12_menus_hud.md` — main menu (which title01.anm scripts, cursor/selection logic, interrupts sent, sub-menus:
   difficulty, character/team select, practice, option, replay, music room as far as needed), pause menu, and the HUD
   (front.anm layout: score, hiscore, lives, bombs, power, graze, point, time, gauge, boss life bar, spell-card name/
   bonus display, stage title). Include when th08logo.jpg is shown.

Tools: extend your tools so every data file touched here parses with 0 problems. Finish with: produced files, what is
VERIFIED vs INFERRED, open questions.
