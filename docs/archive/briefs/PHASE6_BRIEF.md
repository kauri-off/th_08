# Clean-room brief — Phase 6: persistence (replay, score.dat, cfg), endings and result screens

Same role and rules as before (TASK_TEMPLATE.md, RE_WORKFLOW.md). Continue in your SPEC_DIR: re-read NOTES.md,
symbols.csv, structs.md and specs 00–14 + answers_phase5.md first.

Behaviour per frame, struct tables, short pseudocode; never paste decompiled code. Mark VERIFIED/INFERRED.

Deliverables (ONLY these three; finish and verify one before the next):
1. `15_files_replay_score.md` — on-disk formats and their code paths, byte-exact:
   - `th08.cfg`: every field, defaults, validation, when it is read/written.
   - `score.dat`: container/encryption/compression, every chunk type (high scores per difficulty/character,
     clear flags, spell-card history per card (attempts/captures/max bonus), practice scores/unlocks, play time
     and play counts, Extra/Last Word unlock conditions), checksum, when each field is updated, the default table
     written when the file is missing.
   - `replay/th8_*.rpy`: header, encryption/compression, per-stage records (link to 11 §6), input-frame format,
     how input is recorded and played back each frame (incl. slowdown/fps bytes), save flow (which screen asks,
     file name rules), load flow and replay menu listing.
2. `16_endings_result.md` — game-end screens: ending selection (good/bad per character team and path, Extra/
   game-over cases), ending script files and their opcodes/text/picture/music flow, staff roll script, the
   result/score-registration screen (name entry charset, cursor rules, ranking insert, display), "All Clear"
   and Extra-unlock messages, return-to-title flow. Also music room (track list, comments text source, play
   behaviour) and spell practice / Last Word selection details that 12 §2.6 left INFERRED.
3. `answers_phase6.md` — answer the open items still listed in `/home/anon/Projects/th_08/docs/QUESTIONS.md`
   that answers_phase5.md did not close (you may read that file only), plus: who sets spell flags 10/11, and
   glyphs 0xD–0xF in large score popups. Correct earlier specs in place where wrong and list the changes.

Use any tools that get the result (REA, Ghidra, scripts, runtime). Extend your parsers so every data file touched
here (ending scripts, staff roll, music comments, a real score.dat/rpy if present in the game dir) parses with 0
problems. Finish with: produced files, what is VERIFIED vs INFERRED, open questions.
