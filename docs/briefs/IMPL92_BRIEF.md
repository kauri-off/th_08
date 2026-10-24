# IMPL92 — enemy appearance: youkai colour2 / z, aura ops, ANM script start (visible CODE BUGs) — local task

Source: `specs/changelog/answers_re_q32.md` §3 items 6, 8; `answers_re_q33.md` §3 items 11, 12. Implement from the cited
numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be
tested without game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL92_QUESTIONS.md`.

## Deliverables

1. **Enemy colour / z** (07 §10.1 step 7, §10.6): flags A bit 11 → colour2 (0x20, 0x20, 0xC0, alpha / 2) in the step-7
   tail; the colour2 flag is turned off on every frame without a new hit flash; enemy VMs drawn at z 0.25 / 0.3.
2. **Aura ops** (07 ops 80 / 81 / 174): ops 80/81 bit 1 switch the aura's colour2 flag; op 174 sends the aura
   interrupt (mode + 1, mode ≠ 0) and negates the spin for odd slots.
3. **ANM script start without reset** (07 §9.3 and the op 54/57/58/61/62 rows): these ops and the direction
   animations start scripts the `AnmFile_SetScript` way, keeping VM pos / pos offset.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Report the golden
draw summary line before and after, plus the enemy.anm / stg1enm / stg2enm group lines.
