# IMPL131 — float operation order (RE-Q56) — local task

Source: `specs/changelog/answers_re_q56.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL131_QUESTIONS.md`.

## Deliverables

1. **AH** (08 §4.2): `bullet.rs` `update_bullet` states 2–4: `pos += vel * f32(1/d)` (reciprocal rounded to f32 first).
2. **AI** (07 §5.6): `eclvm.rs` interpolation fn 7 (Hermite): product and sum order exactly as in the spec.
3. **AJ** (07 §9.3): `bullet.rs` `pattern_angle` modes 2 and 4 term order per the corrected rows (replaces the RE-Q54 order).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_131`
(22 replays, all must stay identical) and `target/batch_run.sh target/batch_131` (490 recordings, ~20 min; read-only
input): report the identical count and the regression list (must be empty). Do not chase other divergences. Report the
SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
