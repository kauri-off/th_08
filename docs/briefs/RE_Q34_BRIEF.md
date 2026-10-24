# RE-Q34 — implementer questions IMPL91–98

Answer the open questions the implementers filed while porting the RE-Q32/Q33 CODE BUG lists. Each answer goes into a
numbered spec (specs/00–16_*.md, specs/structs.md) and specs/changelog/answers_re_q34.md; say per question whether
the port (current master) is right or a CODE BUG. Use the existing q32/q33 tooling (rungolden.sh, drawlog, probe).

## Questions
1. ECL / enemy: `docs/briefs/IMPL91_QUESTIONS.md`, `IMPL92_QUESTIONS.md`.
2. Effects / stage / stage transition: `IMPL93_QUESTIONS.md`, `IMPL95_QUESTIONS.md`.
3. HUD: `IMPL96_QUESTIONS.md`, `IMPL97_QUESTIONS.md` (who issues HUD message types 2, 3, 4), `IMPL98_QUESTIONS.md`.

## Output
Specs + changelog; short RE-Q34 section in re/NOTES.md; keep re/work/runs/q34/CHECKPOINT.md current (rate limits
happen); end with the CODE BUG list (spec § per item).
