# IMPL133 — orbit effects release, result states (RE-Q56) — local task

Source: `specs/changelog/answers_re_q56.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL133_QUESTIONS.md`.

## Deliverables

1. **AL** (07 §7 row 127, 13 §2.6b): `eclvm.rs` op 127 with slot < 0 releases the boss op-128 orbit effects (fade + free their effect-pool slots; drain `fx_attached`).
2. **Q4a + Q4c** (16 §2.1 "Initial state", §2.4 Exit): `result.rs` — 0x11 (after the practice hiscore) and 0x16 become 10 in `on_register`; `exits` keeps only state 2 at frame > 19; remove the result.rs SPEC-GAP from IMPL129.
3. **Q4b** (16 §2.6): `result.rs` `save_ask` — state 10 → 11 keeps the frame counter (the "cannot save" message takes input after 10 frames, not 20).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_133`
(22 replays, all must stay identical) and `target/batch_run.sh target/batch_133` (490 recordings, ~20 min; read-only
input): report the identical count and the regression list (must be empty). Do not chase other divergences. Report the
SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
