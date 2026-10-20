# IMPL40 — pause/continue menu, Gui face −1, night-clock ops (RE-Q25 CODE BUGs 7–9)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q25.md` (CODE BUG list items 7–9) for pointers.

## Deliverables

1. **Pause / continue menu** (12 §3, §4): drawn in the playfield viewport with the capture VM; difficulty sprite
   0x120 only for ids ≥ 205 (pause menu and HUD); continue "Yes" is the default only while Gui flags bit 9 is clear.
2. **Gui player show with face −1 still restarts VMs 2/4** (12 §5.8).
3. **Night-clock ops 179/180 and the player-overlap fade** (12 §5.7).

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, demo/menu/golden/selftest1 draw logs,
  SPEC-GAP, before → after; raise thresholds, never lower. No trace metric may drop.
- `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL40_QUESTIONS.md`. Work files under `target/impl-work/impl40/`.
