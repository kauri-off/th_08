# IMPL76 — Timer_Sub slow path, enemy step 6 bomb skips, f32 item collection (audit 78–80) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.2 (found by RE-Q29, `specs/changelog/answers_re_q29.md`). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 78** (05 §2): the `Timer_Sub` slow path (speed ≤ 0.99) sets previous := current; the fast path does not.
2. **Audit 79** (07 §10.1 step 6): (a) the whole step is skipped while flags A bit 31 is set and the player is bombing;
   (b) the first `Player_DamageAgainst` call is not made while a card is active, the enemy has a parent and the player
   is bombing.
3. **Audit 80** (08 §8.4): item collection compares f32 box edges (item ± C/2 against the player box stored by
   `Player_Move`), with f32 rounding, instead of |d| ≤ sum of halves.
