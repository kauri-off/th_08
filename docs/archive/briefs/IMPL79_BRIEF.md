# IMPL79 — PlaceBullet angle, CancelBonus lasers, bullet template sprites (audit 83, 89, 94, 104) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.3 (found by RE-Q30, `specs/changelog/answers_re_q30.md` §3). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 83** (08 §3.2, 07 §9.3): `PlaceBullet` velocity = polar of the **unwrapped** pattern angle; only the stored
   angle is wrapped.
2. **Audit 89** (08 §7): `BulletMgr_CancelBonus` cancels every alive laser with no flag-bit-2 test (only `CancelAll`
   tests it), and sets the cancel guard (10).
3. **Audit 94 + 104** (08 §2.1, 05 §2, 08 §3): bullet types 16 / 17 (scripts 111 / 112) have hitbox 4 and class 4;
   bullet +0x218 at spawn holds the template's base (uncoloured) sprite, not the coloured one.
