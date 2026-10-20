# IMPL35 — spell card ring and bonus, bomb-area cancel item (RE-Q27 CODE BUGs 1–3)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts come from the numbered specs only; the changelog
`specs/changelog/answers_re_q27.md` §1 and its CODE BUG list say where to look.

## Deliverables

1. **Capture/start ring follows the boss** (07 §11.1 `Spell_Start` ring + `Spell_Calc` step 1.6, 13 §2.7, 12 §5.8):
   spawn the ring at the boss position (e+0x2D34), not the final position; during the card the centre moves by
   (boss pos + offset − centre)/16 per frame unless spell bit 6, z := 0. Expected: golden 8105 → ~8177,
   fullrun_noclip 7553 → ~7625.
2. **Spell bonus decays per frame** (07 §11, §11.1 step 1.3): −= trunc((R/60)·gs), then rounded down to a multiple of
   10, only while capture is possible (and not bit 11 / flag A bit 27); `Spell_AddBonus` raises R by n/120 below the
   max and caps the bonus at the max. Expected: golden → ~8298, fullrun → ~7746.
3. **`in_bomb_area` does not reset the cancel item** (08 §4.1, 09 §8): +0xE2A90 := 6 only at the start of the hit /
   graze / no-bomb hit tests; the bomb-area test is a pure point test (size argument ignored). Expected: demo 0
   4451 → ~4629.

## Verification

- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, demo and menu draw logs, golden draw log,
  SPEC-GAP count, before → after; raise the test thresholds to the new values (never lower any).
- `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- New questions (if a divergence moves somewhere the spec does not explain) go to `docs/briefs/IMPL35_QUESTIONS.md`.
- Work files under `target/impl-work/impl35/`.
