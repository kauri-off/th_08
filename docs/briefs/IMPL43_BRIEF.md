# IMPL43 — root damage forwarding, death effects for every mode, burst angle (RE-Q28 CODE BUGs 3–5)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q28.md` (CODE BUG list).

## Deliverables

1. **Root damage forward** (07 §10.1 step 6, enemy.rs `damage`): skip while bombing; rd = d/2; root damage timer →
   rd/9 for a boss else 0; floor = max(0, thresholds); only if rd ≠ 0; life ≤ floor → floor.
2. **Death effects for every death mode** (07 §10.3, enemy.rs `death`): sfx + effects + time orb also for mode 3
   (and 4–7); both effect spawns only when e+0x3310 ≥ 0. Expected golden ~10533, fullrun ~9363.
3. **Burst effect 21/26 angle** (13 §2, effect.rs): random (FloatRange(2π) − π) only when param.x ≤ −990.0, else
   `Angle_AddNormalize(param.x)`. Expected golden ~10707, fullrun ~9408.

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, draw logs, SPEC-GAP, before → after; raise
  thresholds, never lower. `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL43_QUESTIONS.md`. Work files under `target/impl-work/impl43/`.
