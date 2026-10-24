# IMPL101 — alpha-0 glyphs, HUD timer across stages, Hud_StageTransition, op 88 on self (RE-Q34 CODE BUG 4–7) — local task

Source: `specs/changelog/answers_re_q34.md` CODE BUG list items 4–7. Implement from the cited numbered-spec sections
only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be tested without game
data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL101_QUESTIONS.md`.

## Deliverables

1. **Alpha-0 glyphs** (05 §9, 12 §5.4): ascii glyphs whose alpha is 0 are not drawn.
2. **HUD timer state + stage transition** (12 §5.1, §3, §5.7, 11 §4): HUD +0x24 / +0x28 cleared only on a fresh
   start, kept across later stages and continues; add `Hud_StageTransition` (clear frame, pause retry, continue retry)
   which queues the second playfield capture that the stage-start tiles show.
3. **Op 88 on the calling enemy** (07 §5.4): works on the running context (thread if one runs), its own stack and
   working depth; pushed ip = stored ip + instruction size; the called sub never runs (local ip written back), the
   other effects stay (clock 0, wait 0, sub id, args, pushed frame, depth + 1). Remove the impl91 SPEC-GAP.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Before = current
master: same 8070147 (99.87 %), changed 10053, missing 249, extra 112, reordered 30597, identical frames 19792.
