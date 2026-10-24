# IMPL102 — SPEC-GAP batch 1 (ECL / enemies): natives 24 / 16, unreachable ECL fixes, close answered markers — local task

Source: `specs/changelog/answers_re_q35.md` (one row per marker of `docs/specgaps/batch1_ecl_enemy.txt`). Implement
from the cited numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`;
unit tests. New open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL102_QUESTIONS.md`.

## Deliverables

1. **Natives 24 and 16** (07 §12 rows 24 / 16, 11 §5): native 24 sets var 10000 to the spell cards captured in this
   game (stats +0x1C); native 16 copies the caller's int var 10007 into each marked child's int var 10007, distance
   test 3D and strict (< 4096).
2. **Unreachable ECL paths** (07 §6, §4.2, §5.5): an int read of 10033 draws one random number and truncates; the
   interrupt table defaults to 0 (unregistered index enters sub 0; a negative entry still does skip / push / depth / pending
   reset); interrupts are dispatched in thread contexts too.
3. **Close the markers RE-Q35 answered "right"** (eclvm 724, 1217, 1239, 1250, 1344, 1364, 1415, 1439, 1851; enemy 878,
   1635, 2530): replace each `SPEC-GAP` with a short spec-ref comment, changing code only where the answer says so.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Report the
SPEC-GAP count after (was 105).
