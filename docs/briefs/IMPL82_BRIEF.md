# IMPL82 — shot box edges, quitting frame, bomb cooldown (audit 84, 97, 98) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.3 (found by RE-Q30, `specs/changelog/answers_re_q30.md` §3). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 84** (09 §4.5): player shot vs enemy overlap uses f32 box edges (min = c − s·0.5, max = s·0.5 + c,
   inclusive).
2. **Audit 97** (15 §2.2, 00 §2): on the frame the calc chain returns quit, nothing is drawn and nothing is presented.
3. **Audit 98** (09 §1.1): the bomb cooldown +0xE2A6C is decremented inside `update_bomb` and skipped on a forced
   start.
