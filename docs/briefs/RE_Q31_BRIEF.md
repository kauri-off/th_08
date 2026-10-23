# RE-Q31 — fullrun from 90010, IMPL78–82 questions

Read `docs/briefs/RE_WORKFLOW.md` first, then `re/work/runs/q30/CHECKPOINT.md`. Answers go into the numbered specs;
changelog `specs/changelog/answers_re_q31.md` with SPEC FIXED / CODE BUG / NEW FACT labels and the CODE BUG list at the
end. Never edit `src/`, never run git. Scratch port: `re/work/runs/q31/portfix/`, copied from the current `src/`.

Master now (1a2cbe5): RE-Q30 fixes J, K, L, N, O, P, Q, S, U, V are merged (impl79–82); M (Vec3_FromPolar), R and T
(f32 laser / player boxes) are being implemented locally as impl83 in this same checkout (`src/` may change under
you, so copy it once at the start). Ops 90–92 (audit 96, 101, 102) are not merged. Golden full, demos in sync,
selftest1 full, fullrun_noclip 90009.

## Questions

1. **fullrun_noclip 90010** and on: root-cause the first divergence (if it is M / R / T, apply them on scratch from
   `re/work/runs/q30/q30_fixes.diff` and go on), confirm on scratch, chase further, give after-fix numbers. Also settle
   the RE-Q30 open item: `Enemy_ChainUnlink` for a root — does the first child keep its prev (07 §10.3a)?
2. Answer `docs/briefs/IMPL78_QUESTIONS.md` (op 128 `d`) and `IMPL80_QUESTIONS.md` (native 8 e+0x2CA0 of a member
   that is not running; stale index with no leader) in the numbered specs.
3. Write `re/work/runs/q31/CHECKPOINT.md` before stopping (rate limits happen), and the final CODE BUG list.
