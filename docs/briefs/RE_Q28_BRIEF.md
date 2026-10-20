# RE-Q28 — next sync divergences after the RE-Q27 fixes

Read `docs/briefs/RE_WORKFLOW.md` first. Same rules as RE-Q27: answers go into the numbered specs, changelog
`specs/changelog/answers_re_q28.md` with SPEC FIXED / CODE BUG / NEW FACT labels and the CODE BUG list at the end.
Never edit `src/`.

The RE-Q27 CODE BUG fixes 1–6 are being implemented in `src/` (impl35/impl36). For root-causing, refresh your scratch
port (`re/work/runs/q27/portfix/` → `re/work/runs/q28/portfix/`) from the current `src/` and re-apply the
`portfix.diff` fixes 1–6 there.

## Questions

1. **golden 8298 and fullrun_noclip 7746** (after fixes 1–2): 8 RNG draws fewer and 1 bullet instead of 2. Root-cause
   and fix the spec.
2. **Demos after the fixes**: demo 0 4629, demo 1 3880, demo 2 4036, demo 3 6665. Root-cause each first divergence
   (the same cause may cover several).
3. **selftest1 1540** (frame counter after a pause-quit, 11 §2): confirm it is only a CODE BUG, give the exact step,
   and find the next selftest1 divergence after it on the scratch port.

Confirm each root cause on the scratch port as in RE-Q27 and give the after-fix numbers.
