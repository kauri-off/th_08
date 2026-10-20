# IMPL38 — spell card ring visuals, silent card end, bonus-line fade (RE-Q27 CODE BUGs 8–9)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q27.md` §2 (IMPL29 Q4/Q5), §4 and the CODE BUG list items 8–9. impl35 left SPEC-GAPs for
the `Spell_Calc` steps not done (1.1, 1.2, 1.4, 1.5, 1.7, failed-ring look) — this task closes them.

## Deliverables

1. **Card ends silently when the boss is gone** (07 §11.1 step 1.1): bit 0 := 0 and `Spell_HideName` when the boss
   is dead or its slot changed.
2. **Ring visuals** (07 §11.1 steps 1.4/1.5/1.7 and capture ring, 13 §2.7): rotation via `Angle_AddNormalize` in
   both branches (inactive / active, last-spell sign), wavy start ring (6 waves, amplitude from VM pos.y while
   +0x334 ≠ 0, 64 → 0 over 100 frames), shrink 256 → 8 over the rest of the card, failed-ring look once capture is
   lost (sprite, scale), t 30/60 restyle slot writes, capture restyle colour / waves.
3. **Bonus-line tint fade** (12 §5.8, 07 §11.1 step 1.2): alpha +0x2623 fades between 0x80 and 0x20 by 4 per frame
   with the player under the boss name (x ≥ 64, y < 64).

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, demo/menu/golden/selftest1 draw logs,
  SPEC-GAP, before → after; raise thresholds, never lower. Trace metrics should not drop; the golden draw log should
  rise.
- `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL38_QUESTIONS.md`. Work files under `target/impl-work/impl38/`.
