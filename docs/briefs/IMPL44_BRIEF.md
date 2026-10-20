# IMPL44 — DropAttracted, single-kill gauge, graze orbs (RE-Q28 CODE BUGs 6–8)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q28.md` (CODE BUG list).

## Deliverables

1. **`ItemMgr_DropAttracted`** (09 §6.1, 08 §8.4) at the end of `Player_Die` (both paths, also the dissolve-mode early
   return) and after the real-death drops: state-1 items → state 0, vel (0, −0.9, 0). Remove the SPEC-GAP. Expected
   demo 0 ~5246.
2. **Single-kill gauge** (07 §10.3a, 13 §4, enemy.rs `kill_single`): `GaugeAdd(−gauge/12, not forced)` — nothing while
   bombing, clamped. Expected demo 1 ~4155.
3. **Graze orbs** (09 §9.2, player.rs `on_graze`): the third orb only inside the bullet-and-card branch. Expected
   demo 2 ~4641.

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, draw logs, SPEC-GAP, before → after; raise
  thresholds, never lower. `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL44_QUESTIONS.md`. Work files under `target/impl-work/impl44/`.
