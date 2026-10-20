# RE-Q25 — answer the implementer questions (IMPL26, IMPL27)

Read `CLAUDE.md` (repo root), `docs/briefs/TASK_TEMPLATE.md` and `docs/briefs/RE_WORKFLOW.md` first.

## Deliverables

1. **IMPL26_QUESTIONS** (ANM, graphics, MSG, HUD, ASCII menus: code vs spec questions and uncited code): for each, say whether the spec or the
   code is right, with evidence (binary and/or a trace/probe run). Fix the numbered spec where it is wrong or silent.
2. **IMPL27_QUESTIONS** (menus, files, replay, input, audio): answer every question the same way, including the spec cross-reference error it reports.
3. **Changelog**: `specs/changelog/answers_re_q25.md` listing, per question, the answer in one line, the spec § changed and
   the evidence. Each answer must be readable from the numbered spec alone.

Mark each answer as one of: SPEC FIXED (the code follows a wrong spec), CODE BUG (the spec is right, so the code must
change), or NEW FACT. Put the CODE BUG list at the end; it becomes the next implementer brief.

Do not touch `src/` and do not run git.

Format and level of evidence: like `specs/changelog/answers_re_q24.md`. Priority: questions that change draw logs or sync
(IMPL26: draw mode 5 depth / mode 4 billboards, MSG op 14 flash, continue-menu default, spell-bonus replay exclusion,
menu viewport/capture; IMPL27: key-repeat timing, replay stage scores, menu screen frame timing, option volume steps).
