# Clean-room brief — Phase 5: sound effects, effects, bombs/options, implementer questions

Same role and rules as before (TASK_TEMPLATE.md, RE_WORKFLOW.md). Continue in your SPEC_DIR: re-read NOTES.md,
symbols.csv, structs.md and specs 00–12 first.

Behaviour per frame, struct tables, short pseudocode; never paste decompiled code. Mark VERIFIED/INFERRED.

Deliverables (ONLY these three; finish and verify one before the next):
1. `13_sfx_effects.md` — sound effects: the SE table (index → wav file in th08.dat, volume/pan/priority), the
   play/queue functions and per-frame dedup rules, every gameplay call site (shots, graze, item collect, extend,
   death, bomb, enemy damage/death, bullet fire sounds per ECL op, menu cursor/select/cancel, spell card, timeout tick).
   Effect manager: struct, max count, effect types (which effNN.anm / ANM script each uses, motion, lifetime),
   every spawn site (hit sparks, enemy death bursts, player death rings, item/bonus text, spell-card backgrounds,
   screen shake/flash), and how it is drawn (layer/order).
2. `14_bombs_options.md` — complete per-character bomb choreography for all 16 bombs + the dissolve spell
   (objects: positions, speeds, spawn timing, ANM scripts, area placement per frame, sounds/effects);
   player options for every shot type (draw scripts, offsets, focus swap, functions 0x44E3A0, 0x44EE70, 0x44F2D0,
   0x44F5E0); player laser (Alice) update funcs 4/5: length, trail, damage rects, end condition;
   shot sprite rotation rule, youkai red tint colour, focused hitbox marker sprite.
3. `answers_phase5.md` — answer every item in `/home/anon/Projects/th_08/docs/QUESTIONS.md` (you may read that
   file only) with VERIFIED/INFERRED; correct earlier specs in place where they were wrong and list the changes.

Tools: extend your tools so every data file touched here parses with 0 problems. Finish with: produced files, what is
VERIFIED vs INFERRED, open questions.
