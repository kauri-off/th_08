# IMPL136 — Reimu bomb orb angles, sin/cos rounded once (RE-Q58) — local task

Source: `specs/changelog/answers_re_q58.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL136_QUESTIONS.md`.

## Deliverables

1. **AQ + AR** (14 §2.1, §2.2): `bomb.rs` `bomb_reimu` / `bomb_reimu_ls` — the ±π/60 spin is a wrapped add
   (Angle_AddNormalize); `reimu_orbs` start angles are a running f32 sum a := −π, a += f32(π/8) per orb (Yuyuko keeps
   −π + i·π/8).
2. **AS** (07 op 32/33, 05 §10): `eclvm.rs` op 32/33 compute sin/cos in f64 and round once to f32; `stage.rs` sway per
   06 §7 (f32(sin φ · k) rounded once; mode 3 up.z).
3. **AS, other logic sites** (05 §10 table): `player.rs` `laser_test`; `bomb.rs` `Area::hits_enemy`, `Area::contains`;
   `bullet.rs` `cancel_lasers`; `effect.rs` `type_init` (17/18/27, burst) and `update` (orbit 13); `anmvm.rs` ops 61/62
   — same once-rounded sin/cos. One shared helper is fine. Draw-only sites are optional; leave them unless trivial.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_136`
(22 replays, all must stay identical) and `target/batch_run.sh target/batch_136` (490 recordings, ~20 min; read-only
input): report the identical count and the regression list (must be empty). If a site in deliverable 3 causes a
regression, revert that site and report it. Report the SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
