# IMPL87 — enemy orbit movement through Vec3_FromPolar (RE-Q31 fix A) — local task

Implement from the cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without
game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL87_QUESTIONS.md`.

## Deliverables

1. **Move mode 3** (07 §10 movement table, mode 3 row; 05 §10): the orbit offset is `Vec3_FromPolar`(orbit angle, r)
   — cos / sin and the product in double, one rounding to f32 (`bullet::polar` after impl83) — not f32(cos)·r.
   Expected: fullrun_noclip moves past row 90010 (to about 98550).
2. Raise the `fullrun_noclip` threshold in `src/session.rs` `MIN_LEADING` to the new leading-row count.
