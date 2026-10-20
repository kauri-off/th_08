# IMPL36 — time parity, Remilia option orbit, GM running flag (RE-Q27 CODE BUGs 4–6)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts come from the numbered specs only; see
`specs/changelog/answers_re_q27.md` §1 and its CODE BUG list.

## Deliverables

1. **`add_time` updates the parity accumulator for negative amounts too** (11 §1.5 setters, stats table +0x44):
   time_added += n also when n < 0 (unless clamped). Expected: demo 1 3870 → ~3880, demo 2 3082 → ~4036.
2. **Remilia options orbit when the option timer is > 12**, not ≥ 12, for team and solo shots (14 §3 table, §3.2).
   Expected: demo 3 1606 → ~6665.
3. **GM flags bit 2 ("running") is recomputed every `GameMgr_Calc` at step 7**, after the pause test and before the
   step-8 return (11 §2.1 flags row 2, §4 step 7). Expected: selftest1 1423 → ~1540.

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, demo and menu draw logs, golden draw log,
  SPEC-GAP count, before → after; raise the test thresholds (never lower any).
- `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL36_QUESTIONS.md`. Work files under `target/impl-work/impl36/`.
