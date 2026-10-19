# IMPL22: boss phase transitions, demo 2 child wait, menu answers

Deliverables:
1. Apply `specs/answers_boss_phases.md` and the updated 07 §4.3/§5.4/§6/§10.1–10.3 (threshold switch order vs damage and same-frame re-run, what the switch keeps/resets, low-life levels, timeout marks the card only, death modes 0–3 incl. mode 3 life := 1 + state 3 for 90, death sub runs next frame, call-stack depth quirk, var 10098 comparison is ≥). Check the stage 1 boss frames listed there against fullrun_noclip (`TH08_SESSION_DUMP`).
2. Demo 2 frame 2261 (answers_impl19 IMPL19 Q3 addendum): the child's first aimed shot is 18 frames early; the wait is `(Next32 & 0x7FFFFFFF) % 30 + 10` with Next32's first draw in the high half (expected 30, port ≈ 12). Find how the port evaluates `imod3` / var 10032 and fix it.
3. Apply `specs/answers_impl17.md` Q1, Q3, Q4, Q6 and Q7 (spell tables / LastWord unlocks / FLSP, menu interrupts, result-viewer/music-room return, text layout, spell practice description + card-name VM) where the port is missing or differs; stub what needs unported scenes and say so.

Then re-measure golden/selftest1/fullrun_noclip `session_sync`, demo `MIN_SYNC`, demo draw %, menus; raise thresholds (never lower without stating why). Questions to `docs/briefs/IMPL22_QUESTIONS.md`.
