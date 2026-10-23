# IMPL85 — threshold-kill death sub, ops 86/87 single getter, enemy timer after death (audit 105, D.2, D.3) — local task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` row 105 and §D items 2, 3. Implement from the cited spec sections only;
spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question to `docs/briefs/IMPL85_QUESTIONS.md`.

## Deliverables

1. **Audit 105** (07 §10.2, §10.6): `kill_non_bosses` (threshold / timeout kill of every non-boss) jumps into the death
   sub with `Ecl_SetSub` only (ip, clock 0, wait 0, sub id), like `KillAll` after impl81 — not the full death reset.
2. **Audit D.2** (07 §7 ops 86 / 87): the boss variable is evaluated once with the getter the op needs (no second
   getter call, so no extra RNG draw for 10032–10035 / 10082); op 86 does not test whether the boss exists, op 87 does.
3. **Audit D.3** (07 §10.1, §10.3): the enemy timer e+0x2E14 tick and the damage-timer decrement happen in step 7,
   after step 6's death handling, so the death bonus seconds use the un-ticked timer.

Mark each finished row: append `✅ impl85` to row 105 and to the D.2 / D.3 items.
