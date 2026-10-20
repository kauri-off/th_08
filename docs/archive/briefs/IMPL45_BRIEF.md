# IMPL45 — GameFlags bit-10 enemy skip, frame counter, exit-save timing (RE-Q28 CODE BUGs 9–11)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q28.md` (CODE BUG list).

## Deliverables

1. **GameFlags bit 10** (07 §10.1 step 0, 11 §2.1, enemy.rs `step`): while set, only the play-time / human-rate
   counters run. Expected demo 3 ~6684, demo 2 ~4660.
2. **Frame counter** 0x164D2C8 := 0 as the last step of `GameMgr_OnRemove` (11 §2). impl37 already resets it in
   `on_remove`; check the step order against the spec and fix if needed.
3. **Exit save timing** (15 §2.2, supervisor.rs): save after the last frame (after the main loop), not inside the
   requested-scene −1 calc. Expected selftest1 full match.

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, draw logs, SPEC-GAP, before → after; raise
  thresholds, never lower. `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL45_QUESTIONS.md`. Work files under `target/impl-work/impl45/`.
