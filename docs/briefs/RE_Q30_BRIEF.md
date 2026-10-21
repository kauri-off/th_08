# RE-Q30 — remaining fullrun divergences, IMPL42–54 questions

Read `docs/briefs/RE_WORKFLOW.md` first, then `re/work/runs/q29/CHECKPOINT.md`. Answers go into the numbered specs;
changelog `specs/changelog/answers_re_q30.md` with SPEC FIXED / CODE BUG / NEW FACT labels and the CODE BUG list at the
end. Never edit `src/`. Scratch port: `re/work/runs/q30/portfix/`, copied from the current `src/` (master 3a3e354:
RE-Q29 fixes A–C and F–I are merged; D and E (audit 75–77, impl75) are not, apply them from `q29_fixes_I.diff`).

Master now: all four demos in sync, golden 11910 (rank sub-counter, impl75), fullrun_noclip 9407 (flags bit 7, impl75),
selftest1 full.

## Questions

1. **fullrun_noclip 29948 and 48756** (after RE-Q29 fixes): 29948 bullet count off by one for one row (a ring
   bullet's velocity from a slightly different angle, freed one frame early); 48756 a shot hit with its time orb one
   frame early. Root-cause, confirm on the scratch port, chase further divergences, give after-fix numbers.
2. Answer the open questions in `docs/briefs/IMPL42_QUESTIONS.md` … `IMPL54_QUESTIONS.md` in the numbered specs (skip
   ones already answered; say which).
3. Close the finished RE-Q29 changelog: add the 29948 / 48756 rows and its final CODE BUG section to
   `specs/changelog/answers_re_q29.md`.
