# IMPL125 — replay route byte, fast-forward screen effects, shake freeze (RE-Q54) — local task

Source: `specs/changelog/answers_re_q54.md` (rows named below; the CODE BUG list names the src functions). Implement from
the numbered specs only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open
details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL125_QUESTIONS.md`.

## Deliverables

1. **S** (10 §4): `hud.rs` `StartInfo.replay_route` — during replay playback the stage-5 route comes from replay header byte +0x11C.
2. **W** (13 §3): `game.rs` `on_restart` / `effect::register_pending` — a screen effect registered in one fast-forward pass runs in the next pass of the same frame.
3. **AA** (13 §3): `effect.rs` `ScreenEffect::frozen` — shakes test the spell-death freeze flag (GameFlags bit 10) directly.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (latest target/pilot_* dir) and after (target/pilot_125).
No session may get worse. Do not chase other divergences. Report the SPEC-GAP count (was 2).
