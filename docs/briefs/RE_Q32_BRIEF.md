# RE-Q32 — draw parity (golden draw log), IMPL86/89/90 questions

Read `docs/briefs/RE_WORKFLOW.md` first, then `re/work/runs/q31/CHECKPOINT.md`. Answers go into the numbered specs;
changelog `specs/changelog/answers_re_q32.md` (SPEC FIXED / CODE BUG / NEW FACT, final CODE BUG list). Never edit
`src/`, never run git. Scratch port `re/work/runs/q32/portfix/` copied from the current `src/`.
Wine is now the system `wine` 11.x with prefix `re/work/wine` (PortProton is gone; the scripts default to it).

Master now (2c3bb84): the logic trace is full on every session (golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). The draw log is not: `cargo run --release --bin session -- specs/data/sessions/golden --out DIR` (with
TH08_DIR) gives 87.9 % identical quads, 723 / 25633 identical frames, first divergence at present 47 (a colour). Main
groups: front.anm#0 3.66 M extra quads (HUD panel drawn when the original does not), ascii.anm#0 545 k changed
(pos, 2D z / zwrite), capture.anm#0 never drawn by the port (from present 10795: the screen-capture effect),
etama.anm#4 / loading00.anm missing, enemy.anm colour, etama.anm#1 colour / state. Report: DIR/index.html.

## Questions

1. Chase the draw divergences in order of size (HUD panel repaint rule first, then ascii text quads, then capture.anm,
   then the rest), each to its numbered-spec section; confirm on scratch with the draw report and give after-fix
   identical-quad / identical-frame numbers. The logic trace must stay full.
2. Answer `docs/briefs/IMPL86_QUESTIONS.md`, `IMPL89_QUESTIONS.md` and `IMPL90_QUESTIONS.md` in the numbered specs.
3. Keep `re/work/runs/q32/CHECKPOINT.md` current (rate limits happen); end with the CODE BUG list.
