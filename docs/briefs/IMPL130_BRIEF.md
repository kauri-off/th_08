# IMPL130 — bullet cancels and item collection (RE-Q56) — local task

Source: `specs/changelog/answers_re_q56.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL130_QUESTIONS.md`.

## Deliverables

1. **AC** (08 §4.1, §7): `bullet.rs` `cancel_all` / `cancel_bonus` bomb-area branch spawns the raw player+0xE2A90 item type with mode 1 (no 9 → two time orbs / −1 → none mapping; that is only the state-1 drop); `cancel_all` calls `in_bomb_area` twice per bullet.
2. **AK** (08 §7 "Slot zeroed"): `cancel_all` / `cancel_radius` reset the whole bullet slot (incl. off-screen counter +0xDBA); a normal free still resets only state + 2 timers.
3. **AE** (08 §8.4): `item.rs` `calc` — the collected item stays occupied while its type handler runs (power → set power → cancel to items), freed after.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_130`
(22 replays, all must stay identical) and `target/batch_run.sh target/batch_130` (490 recordings, ~20 min; read-only
input): report the identical count and the regression list (must be empty). Do not chase other divergences. Report the
SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
