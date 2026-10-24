# IMPL99 — in-place int ops, draw-log tooling (remaining RE-Q32 CODE BUGs) — local task

Source: `specs/changelog/answers_re_q32.md` §3 items 16–17; `docs/PARITY_POLICY.md`. Implement from the cited
numbered-spec sections only; spec-ref comments per `CLAUDE.md`; unit tests. Open details: one-line `// SPEC-GAP:` plus
a question in `docs/briefs/IMPL99_QUESTIONS.md`.

## Deliverables

1. **In-place int ops** (07 §6): read and write go through the variable reference (the instruction's own argument
   slot), not the getter, also for non-int destinations such as 10042–10044.
2. **Draw-log writer** (specs/data/drawlog/FORMAT.md §2): fog start / end printed like C `%g` (6 significant digits),
   as the probe does.
3. **Draw-log comparator** (FORMAT.md §3, PARITY_POLICY): reference batches cut at 682 quads (`P list 4`) are treated
   as truncated (port quads beyond the cut are not counted as extra); the report lists "accepted" groups separately
   from real divergences — the front.anm side-panel per-frame repaint (RE-Q32 CODE BUG 1, not ported by policy).

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Report the
golden draw summary after (with and without accepted groups).
