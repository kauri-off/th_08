# IMPL37 — pause-quit frame counter, ASCII counter, mode-0 boss marker (RE-Q27 CODE BUGs 7, 10 + selftest1 1540)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q27.md` (§1 selftest1 row, §3 IMPL30, CODE BUG list).

## Deliverables

1. **selftest1 row 1540: frame counter after a pause-quit** (11 §2): the trace's frame counter reads differently
   after quitting from the pause menu; RE-Q27 says 11 §2 already describes the correct value. Implement it.
   Expected: selftest1 1539 → higher.
2. **ASCII manager frame counter +0x8284** (12 §5.10): += 1 at the end of every `Ascii_Calc`, never reset, and the
   boot calc passes do not count (it equals the main-menu frame number). Fixes the boss-marker blink one frame
   early in golden (check the golden draw log).
3. **Mode-0 boss keeps its marker** (12 §5.10, 07 §10.3 rows 0–1): a boss killed with death mode 0 keeps its boss
   table entry and flag; the death frame still updates the marker, later frames skip the dead slot, so the marker
   stays at its last position until op 127 −1, a new op 127 on the slot, or the next stage. Do not unregister in
   `release()` for that case.

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, demo/menu/golden draw logs, SPEC-GAP,
  before → after; raise thresholds, never lower.
- `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL37_QUESTIONS.md`. Work files under `target/impl-work/impl37/`.
