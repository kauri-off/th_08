# IMPL124 — enemy manager: aimed-enemy filter, time-rank clock, live game speed (RE-Q54) — local task

Source: `specs/changelog/answers_re_q54.md` (rows named below; the CODE BUG list names the src functions). Implement from
the numbered specs only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open
details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL124_QUESTIONS.md`.

## Deliverables

1. **U** (14 §3.1): `enemy.rs` `update_body` / `offer_aimed` — only enemies with flag A bit 6 (shootable) are offered as Yukari's aimed enemy.
2. **V** (11 §3.2): the +100 time-rank tick uses the enemy manager's clock at game speed.
3. **Y** (07 §5): `enemy.rs` `update` / `update_body` — timers read the game speed at each tick (live), so a slowdown set by this frame's script applies at once.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (latest target/pilot_* dir) and after (target/pilot_124).
No session may get worse. Do not chase other divergences. Report the SPEC-GAP count (was 2).
