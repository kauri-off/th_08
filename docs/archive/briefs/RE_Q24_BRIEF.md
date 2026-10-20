# RE-Q24 — answer the implementer questions (IMPL22, IMPL23, IMPL24)

Read `CLAUDE.md` (repo root), `docs/briefs/TASK_TEMPLATE.md` and `docs/briefs/RE_WORKFLOW.md` first.

## Deliverables

1. **IMPL24_QUESTIONS** (code vs spec mismatches Q1–Q10 and the uncited code): for each, say whether the spec or the
   code is right, with evidence (binary and/or a trace/probe run). Fix the numbered spec where it is wrong or silent.
2. **IMPL22_QUESTIONS and IMPL23_QUESTIONS**: answer every question the same way.
3. **Changelog**: `specs/changelog/answers_re_q24.md` listing, per question, the answer in one line, the spec § changed and
   the evidence. Each answer must be readable from the numbered spec alone.

Mark each answer as one of: SPEC FIXED (the code follows a wrong spec), CODE BUG (the spec is right, so the code must
change), or NEW FACT. Put the CODE BUG list at the end; it becomes the next implementer brief.

Do not touch `src/` and do not run git.
