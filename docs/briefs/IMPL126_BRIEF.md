# IMPL126 — invuln timer reset, pattern angle order (RE-Q54) — local task

Source: `specs/changelog/answers_re_q54.md` (rows named below; the CODE BUG list names the src functions). Implement from
the numbered specs only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open
details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL126_QUESTIONS.md`.

## Deliverables

1. **Z** (09 §6.4): `player.rs` `update_invuln` — leaving post-respawn invulnerability sets the state timer to exactly 0.
2. **AB** (07 §9.3): `bullet.rs` `pattern_angle` — fans (modes 0/1) add (k + aim) + a1; ring modes 2/4 add aim in their own order as the spec gives.
Expected after this task: all 22 pilot sessions identical to the end (RE-Q54 fixAB).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (latest target/pilot_* dir) and after (target/pilot_126).
No session may get worse. Do not chase other divergences. Report the SPEC-GAP count (was 2).
