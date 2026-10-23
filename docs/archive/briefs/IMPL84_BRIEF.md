# IMPL84 — ops 90–92 chained children (audit 96, 101, 102) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.3 (found by RE-Q30, `specs/changelog/answers_re_q30.md` §3). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

Needs impl81 merged (it edits `kill_all` / chain code in `enemy.rs`).

1. **Audit 96** (07 §10.5): a chained child that spawns links the new enemy directly after itself.
2. **Audit 101** (07 §10.5): ops 90–92 never write e+0x3330; the spawn-time run sees mode bits 0.
3. **Audit 102** (07 §10.5): op 92 writes the follow offset +0x2D40 / +0x2D88, the aura and bit 9 **after** the
   spawn-time run.
