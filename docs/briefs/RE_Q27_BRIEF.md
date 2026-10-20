# RE-Q27 — next sync divergences, IMPL29/30 questions

Read `CLAUDE.md` (repo root), `docs/briefs/TASK_TEMPLATE.md` and `docs/briefs/RE_WORKFLOW.md` first.

The port now matches golden for 8104 rows, fullrun_noclip 7552, selftest1 1422; demo MIN_SYNC 4450/3869/3081/1605.

## Deliverables

1. **Root cause of each first divergence**, the way RE-Q24 did it (run the original, compare per-frame state/RNG
   sites): golden row 8105, fullrun_noclip row 7553 (both look like time-orb collection timing, see
   `docs/briefs/IMPL29_QUESTIONS.md`), demo 2 frame 3082, and demos 0/1/3 (4451, 3870, 1606) and selftest1 (1423) if no
   numbered spec already explains them. For each: the rule in the numbered spec (fix or add it) and whether the port
   is wrong (CODE BUG).
2. **IMPL29_QUESTIONS and IMPL30_QUESTIONS**: answer every question into the numbered specs (IMPL30 Q1, the boss-marker
   frame counter start, explains the one-frame-early blink).
3. **Changelog**: `specs/changelog/answers_re_q27.md`, same format as `answers_re_q26.md`, CODE BUG list at the end in
   priority order (sync first).

Do not touch `src/` and do not run git.
