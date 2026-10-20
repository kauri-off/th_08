# IMPL39 — demo-end fade timing, stage-clear panel, HUD viewport and repaint (RE-Q25 CODE BUGs 4–6)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q25.md` (CODE BUG list items 4–6) for pointers.

## Deliverables

1. **Screen effects registered from `GameMgr_Calc` get their first calc in the same frame** (13 §3) — e.g. the
   demo-end fade.
2. **Stage-clear panel per 12 §5.6** (rewritten by RE-Q25): calc vs draw conditions, colours, layout, integer maths.
3. **HUD viewport and repaint** (12 §5.3, §5.5): everything drawn before `Hud_DrawPanel` uses the playfield
   viewport; the blank patch at (512, 464) and the tile-13 full-repaint rule; spell-bonus line positions.

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, demo/menu/golden/selftest1 draw logs,
  SPEC-GAP, before → after; raise thresholds, never lower. Draw logs should rise; no trace metric may drop.
- `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL39_QUESTIONS.md`. Work files under `target/impl-work/impl39/`.
