# IMPL134 — homing bullets, Alice option during bomb, Sakuya bomb follow write (RE-Q57) — local task

Source: `specs/changelog/answers_re_q57.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL134_QUESTIONS.md`.

## Deliverables

1. **AM** (09 §4.4): `pshot.rs` `bullet_update_fn` update 1 (homing): steering and speed-up only in state 1 (state 2 only angle = atan2); speed-up rescales by the current |v| = sqrt(vx²+vy²).
2. **AN** (14 §3 row 0x44EA40, 09 §5): `pshot.rs` `init_option` Alice — position set only when not bombing; created during a bomb she stays at (0,0,0) until the bomb ends (her laser follows).
3. **AO** (14 §2.7/§2.8, 13 §2.6a): `bomb.rs` `bomb_sakuya` (and LS) follow write into the effect saved at T = 0 has no alive/type check; for 3D particle kinds 19/51/63 that write must not change their world position (split pos vs world in `effect.rs` per 13 §2.6a, or the equivalent).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_134`
(22 replays, all must stay identical) and `target/batch_run.sh target/batch_134` (490 recordings, ~20 min; read-only
input): report the identical count and the regression list (must be empty). Do not chase other divergences. Report the
SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
