# IMPL135 — replay read past the stream, negative item type, uncapped AddScore (RE-Q57) — local task

Source: `specs/changelog/answers_re_q57.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL135_QUESTIONS.md`.

## Deliverables

1. **AP** (15 §3.3): `replay.rs` `next_frame` / playback calc — past the end of a stage stream keep reading the following words of the decompressed image (no bound check), not 0.
2. **Q1** (08 §8.2 row −1, §8.3 "No type check"): `item.rs` `spawn` — remove the `kind < 0` guard; type byte 0xFF, script −1 + 0x3D, collect = stats bit + sound 0x15 + free, signed type in draw. Closes the IMPL130 SPEC-GAP.
3. **AddScore** (11 §5): `player.rs` `Stats::add_score` has no cap; the cap applies only in GM calc step 9 and on GM unregister (check silentselene/gensokyou_th8_udKa49 in the batch).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_135`
(22 replays, all must stay identical) and `target/batch_run.sh target/batch_135` (490 recordings, ~20 min; read-only
input): report the identical count and the regression list (must be empty). Do not chase other divergences. Report the
SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
