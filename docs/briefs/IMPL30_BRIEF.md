# IMPL30 — draw fixes from RE-Q25 (boss markers, mode-5 depth, MSG flash)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. These are the top three CODE BUG items from RE-Q25
(evidence only: `specs/changelog/answers_re_q25.md`, IMPL26 Q2/Q5/Q10). Follow the numbered specs.

## Deliverables

1. **Boss "ENEMY" position markers** — 12 §5.10 (and §5.9 for the ASCII-manager VMs they live in): the four markers at
   the bottom of the playfield during boss fights, with their creation, position, visibility and removal rules.
2. **Draw mode 5 vertex depth** — 05 §9: use the projected z, not pos z. Mode 4/5 dispatch per the same section.
3. **MSG op 14 flash** — 10 (op 14) and 13 §3: a ScreenEffect type 4 (442 frames, draw prio 21) instead of the
   HUD-drawn flash; remove the HUD path.

## Verification

- Report before/after: golden, fullrun_noclip, selftest1 leading rows (now 8104 / 7552 / 1422); demo MIN_SYNC
  (4450/3869/3081/1605); draw-log percentages for the demos and the menu logs; tests (81). Draw-log numbers should go
  up; nothing may drop without an explanation.
- If the golden session has a draw-log comparison available, use it for the boss markers; otherwise take a screenshot
  of a boss fight and look at it.
- Divergences the spec does not explain → `// SPEC-GAP:` + `docs/briefs/IMPL30_QUESTIONS.md`. Never fit code to a trace.
- Work files under `target/impl-work/impl30/`.
