# IMPL75 — rank sub-counter, GameFlags bits 7/8/13, msg op 11 (audit 75–77) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.2 (found by RE-Q29, `specs/changelog/answers_re_q29.md`). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 75** (11 §3, §3.1): the rank sub-counter (0x164D340) is zeroed at every stage start; `GameMgr_InitRank` sets
   only rank / min / max.
2. **Audit 76** (11 §2.1): GameFlags bits 7, 8 and 13 live in the game flags word (`game.flags`, the trace `flags`
   column); remove the separate `Player::gflags` copy and make every reader and writer use the word.
3. **Audit 77** (10 §5 op 11): the trigger is set only for stage idx 6–8; in stages 1–5 the op only stalls.
