# IMPL127 — op 109, spell-practice start power, result exit frame (RE-Q55) — local task

Source: `specs/changelog/answers_re_q55.md` (CODE BUG list items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL127_QUESTIONS.md`.

## Deliverables

1. **Item 1** (07 §7 row 109, §9.1): `eclvm.rs` `fire_stored` — spawn the stored descriptor directly, origin = pos (e+0x2D34) + shot offset, no filters, no rank add; the descriptor holds what `Ecl_FireBullets` last wrote (decoded, rank-adjusted). Closes the IMPL121 SPEC-GAP.
2. **Item 3** (11 §3.1): `gamemgr.rs` stage start — spell-practice start power 30/80/128 by card id.
3. **Item 6** (16 §2 "Exit"): `result.rs` `calc` — state 2 at frame > 19 returns Remove without running the VMs or advancing the frame, so the score.dat save (2 RNG draws) happens that frame; recheck the draw workaround for frame > 20.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3), plus `cargo run --release --bin session -- sessions/<name> --out target/impl127/<name> --no-drawlog` for
gameover_save and musicroom_practice (read-only input; report leading identical rows before/after). Then
`target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only) into target/pilot_127; no session may get
worse. Do not chase other divergences. Report the SPEC-GAP count.
