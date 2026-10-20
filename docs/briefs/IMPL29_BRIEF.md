# IMPL29 — the three first sync divergences (RE-Q24 code bugs)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. RE-Q24 found the root cause of the first divergence in each
reference session; the numbered specs now state the rule. Fix the code to follow the spec.
(Evidence only: `specs/changelog/answers_re_q24.md`, IMPL22 Q2/Q7/Q8.)

## Deliverables

1. **Capture time reward as time orbs** — 07 §11.1: a captured card's time reward is spawned as time orbs from the
   capture ring, not added directly; the 130-frame payout only adds the score. Expected: golden passes row 8056.
2. **Death shrink timer** — 09 §6.2 (and §6.1–§6.4 as they apply): the shrink timer is not reset at the real death;
   it counts from the hit. Expected: demo 2 passes frame 2938.
3. **Op 67/178 random-move edge tests** — 07 §8.3: the y-edge tests run one after the other (today one `||`,
   `src/eclvm.rs` ~line 594). Check the x tests and op 178 against the same section. Expected: fullrun_noclip passes
   row 6266.

## Verification

- Report before/after: golden, fullrun_noclip, selftest1 leading identical rows; demo MIN_SYNC; draw-log percentages;
  tests (81 now). Every number must go up or stay; explain any drop.
- When a session moves on to its next divergence, give its row/frame and the first differing fields, then stop. Do not
  chase it: list it in `docs/briefs/IMPL29_QUESTIONS.md` with what you saw, for the dirty room. Never fit code to a
  trace.
- Keep work files under `target/impl-work/impl29/`.
