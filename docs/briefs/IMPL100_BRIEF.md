# IMPL100 — large-popup sprite, boss-bar state machine, boss timer draw (RE-Q34 CODE BUG 1–3) — local task

Source: `specs/changelog/answers_re_q34.md` CODE BUG list items 1–3. Implement from the cited numbered-spec sections
only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be tested without game
data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL100_QUESTIONS.md`.

## Deliverables

1. **Large popups** (13 §4): the large-popup VM is initialised with sprite 0x88 (12 px glyphs); remove the impl96
   SPEC-GAP about it.
2. **Boss-bar state machine** (12 §5.1b step 1, §5.1 +0x2C): states 0–3 driven by the label VM's wait-for-interrupt
   flag; alpha 0 on the request frame; instant hide; the fill moves only once the bar is shown; the request is just the
   +0x2C byte (no "boss exists" test); the step is skipped during dialogue.
3. **Boss timer draw** (12 §5.4): drawn on every guarded draw with no timeout gate (remove the impl98 SPEC-GAP); colour
   from the unclamped value; the sound plays when the raw value changes, then +0x28 := +0x24; the draw guard reads
   +0x2C live.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Before =
current master golden draw summary (run it first). Report the summary after plus the ascii.anm#0 line.
