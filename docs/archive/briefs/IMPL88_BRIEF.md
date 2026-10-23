# IMPL88 — spell-practice guard of ops 129/130/133/134, timeline op 9 (audit §B) — local task

Implement from the cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without
game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL88_QUESTIONS.md`.

## Deliverables

1. **Spell-practice guard** (07 §5 ops 129, 130, 133, 134; 11 §2.1 game flags bits 7, 8, 14): in spell practice with
   game-flags bits 7–8 ≠ 0, op 129 and op 130 are ignored, and ops 133 / 134 set the threshold / timeout but not the
   sub. Replace the "Not implemented" note in `src/eclvm.rs`.
2. **Timeline op 9** (07 timeline table op 9, 09 §9.4): `GameMgr_SetPower`(n) — power := n with its checksum / RNG
   step — instead of only counting the call.

Mark the §B text in `docs/AUDIT_SPEC_CONFORMANCE.md` (append `✅ impl88` after "spell-practice guard для ops
129/130/133/134" and "timeline op 9"); add one impl88 entry to `docs/STATUS.md`.
