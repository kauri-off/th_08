# IMPL74 — HUD calc order, stage-clear trigger, clear panel (audit 72–74) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.2 (found by RE-Q29, `specs/changelog/answers_re_q29.md`). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 72** (12 §5.1b): `Hud_Calc` runs `Hud_Update` (bonus, trigger, clock animation, VMs, fade, popup timers)
   first, then `Msg_Run`, so a dialogue op 9 bonus is added on the next frame.
2. **Audit 73** (12 §5.6): the clear trigger is tested before the clock step and has no 60-frame gate.
3. **Audit 74** (12 §5.6): for stage idx > 6 the whole clear panel moves up 16, not only the title.
