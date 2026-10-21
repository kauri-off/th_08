# IMPL77 — screen-shake durations, continue menu first frame (audit 81–82) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.2 (found by RE-Q29, `specs/changelog/answers_re_q29.md`). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 81** (14 header note, §2.3, §2.4, §2.7, §2.8): `ScreenEffect_Register` shake arguments as the spec now gives
   them: Sakuya (1: 120, 4, 1), Sakuya last spell (1: 50, 4, 1), Alice and Alice last spell (1: 24, 8, 0).
2. **Audit 82** (12 §4): the continue menu opens on the frame the game-over flag is seen; the first
   `ContinueMenu_Update` does state 0 and falls into state 2 / 1 in the same call.
