# IMPL132 — spell end bonus, Yukari option, gauge timers (RE-Q56) — local task

Source: `specs/changelog/answers_re_q56.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL132_QUESTIONS.md`.

## Deliverables

1. **AD** (07 §11.1): `enemy.rs` `finish_spell` — at the tail of every Spell_End, after the time-reward test: boss flags A bit 27 := 0, fixed bonus (+4) := 0, bit 11 := 0.
2. **AF** (14 §3.1): `pshot.rs` Yukari option sub-state 3: run the chase whenever the target pointer is set, then the exit test (the option moves on the exit frame).
3. **AG** (09 §9.3): `player.rs` `gauge_drift`: timer B decrements through the game-speed timer decrement; n from the float value of timer C (> 300.0 → 21, else ftol(c/15)).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_132`
(22 replays, all must stay identical) and `target/batch_run.sh target/batch_132` (490 recordings, ~20 min; read-only
input): report the identical count and the regression list (must be empty). Do not chase other divergences. Report the
SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
