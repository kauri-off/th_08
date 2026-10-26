# IMPL123 — ECL: spawn-op life gate, var 10100 remaining time, native 2 bounce (RE-Q54) — local task

Source: `specs/changelog/answers_re_q54.md` (rows named below; the CODE BUG list names the src functions). Implement from
the numbered specs only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open
details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL123_QUESTIONS.md`.

## Deliverables

1. **Q** (07 op 93/94 row, §10.5): `eclvm.rs` `spawn_child` — spawn ops 90–94 do nothing while the spawner's life ≤ 0, checked before any argument is read.
2. **T** (07 §6 row 10100): var 10100 = remaining spell-card time, counting down at game speed and continuing after the card ends (persistent timer in `enemy.rs`).
3. **X** (07 §12 row 2): native 2 flips velocity at the screen edges without a direction check.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (latest target/pilot_* dir) and after (target/pilot_123).
No session may get worse. Do not chase other divergences. Report the SPEC-GAP count (was 2).
