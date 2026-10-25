# IMPL121 — Yukari aim, orbit wrap, ECL bullet-op filters, explosion hit card state (RE-Q53 K–N) — local task

Source: `specs/changelog/answers_re_q53.md`. Implement from the numbered specs only; spec-ref comments per `CLAUDE.md`;
follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question in
`docs/briefs/IMPL121_QUESTIONS.md`.

## Deliverables

1. **Player options** (09 §2.1 init 1, 14 §3 "Orbit wrap", §3.1–§3.3): `pshot.rs` — Yukari's aimed shot targets the
   enemy's `pos` (e+0x2D34), angle = wrap_add(atan2(dy, dx), entry angle + π/2), the option chase keeps the final
   position (K); every orbiting option's angle uses wrap_add (L).
2. **ECL bullet op** (07 §9.1, §9.2): `eclvm.rs` — mode and no-fire filters run on the raw instruction before any
   argument is decoded, in both the op and the auto-fire path; the mode filter reads the enemy's flag A bit 11;
   decode order type, count1, count2, angle1, speed1, angle2, speed2, colour; speed2's rank add applies even when
   speed1 is 0 (M).
3. **Explosion hit filter** (09 §2.1 hit 1): the filter sees the spell-card state at the moment of the damage call,
   not the previous frame's copy; check other `env.spell` reads made during the enemy update the same way (N).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (target/pilot_120) and after. Expected per RE-Q53: 51842
69097, 50715 8951, 80412 79679, 51852 67035, Bi01 21879, 53084 35190. Do not chase other divergences. Report SPEC-GAP
count (was 1).
