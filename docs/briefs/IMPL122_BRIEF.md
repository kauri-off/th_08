# IMPL122 — bombs: Yukari boundary rects, last-spell bomb count, Yuyuko butterflies (RE-Q54) — local task

Source: `specs/changelog/answers_re_q54.md` (rows named below; the CODE BUG list names the src functions). Implement from
the numbered specs only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open
details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL122_QUESTIONS.md`.

## Deliverables

1. **O** (14 §2.13/§2.14): `effect.rs` `boundary_sides` and the kind-37 spin — constant 0x3F3504F2, angle wrap on every side, each rotation chained from the previous side.
2. **P** (09 §7): `bomb.rs` `start_bomb` — last-spell bomb with fewer than 2 bombs zeroes the count with no RNG; only the 2-bomb case draws 4.
3. **R** (14 §2.15): `bomb.rs` `bomb_yuyuko` — a butterfly reaching radius 500 also switches off its two bomb areas; its angle is wrapped.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (latest target/pilot_* dir) and after (target/pilot_122).
No session may get worse. Do not chase other divergences. Report the SPEC-GAP count (was 2).
