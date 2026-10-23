# IMPL80 — natives 8, 9/11/25 (Player_LaserTest), 28/29 (audit 85, 90, 103) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.3 (found by RE-Q30, `specs/changelog/answers_re_q30.md` §3). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 85** (07 §12 native 8): the familiar ring walks from the **parent**, writes int vars 10037 / 10005 / 10006,
   counts calls in int var 10007 and adds the leader's orbit velocity when the counters differ.
2. **Audit 90** (07 §12, 09 §6.1): natives 9 / 11 / 25 call `Player_LaserTest` (implement it per 09 §6.1 if missing,
   f32 box edges): origin = pos − (float vars 10016, 10017), angle = main VM rotation z, a 590-long box from the origin;
   graze with the small box when timer e+0x2E14 changed and % 12 == 0, hit with the big box every call; no warning
   phase.
3. **Audit 103** (07 §12): native 28 sets +0x218 := sprite for every live bullet and sprite := 0x6F only for sprites
   0x60–0x6F; native 29 restores only sprites in 0x60–0x6F; VM0 only.
