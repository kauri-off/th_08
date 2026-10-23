# IMPL81 — EnemyMgr_Calc order, held enemies, KillAll (audit 87, 88, 95, 92, 99, 100) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.3 (found by RE-Q30, `specs/changelog/answers_re_q30.md` §3). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

1. **Audit 87 + 88** (07 §10.1 step 1, 11 §3.2, 07 §7 op 176): `EnemyMgr_TimeRank` runs at the **start** of
   `EnemyMgr_Calc`, before the timelines and the slot loop; the op-176 whole-playfield box goes first inside the bit-10
   gate, before TimeRank.
2. **Audit 95** (07 §10.1 step 2): a held enemy (flags B bit 7, or A bit 30 while bombing / player state ≠ 0) skips
   react, ECL, movement, screen check, VMs, collision and death; only the e+0x2E14 decrement and the common tail run.
3. **Audit 92 + 99 + 100** (07 §7 op 95, §10.3a, §10.6): `EnemyMgr_KillAll` calls `Enemy_ChainUnlink` (original
   semantics, §10.3a) on every enemy it kills; first popup 2000 then +30; final pos recomputed; trail items every 6th
   entry; the death-sub jump is `Ecl_SetSub` (ip, clock 0, wait 0, sub id only); when it hits the caller's own main
   context the local ip continues in the old sub and the write-back overwrites the death-sub ip.
