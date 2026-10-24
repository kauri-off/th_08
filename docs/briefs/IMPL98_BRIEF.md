# IMPL98 — boss bar: op 158 markers, bar target / timer, exact HUD quad coords (visible CODE BUGs) — local task

Source: `specs/changelog/answers_re_q32.md` §3 items 10, 11, 13. Implement from the cited numbered-spec sections only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be tested without game data.
Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL98_QUESTIONS.md`.

## Deliverables

1. **Op 158** (07 op 158 row): word 1 = start (+0x5C), word 2 = end (+0x3C), stored once as f32(a)/f32(max) and
   f32(b)/f32(max) with the op enemy's max life e+0x2E00 (not computed at draw time from the boss).
2. **Boss bar and timer** (12 §5.1, §5.4, 10 §7): boss timer value = HUD +0x24 written by `Enemy_CheckTimeout` (boss,
   slot 0, timeout ≥ 0) before the timer tick; bar target = f32(life e+0x2DFC) / f32(max life e+0x2E00) (no HUD-life
   field, no clamp); remaining-bars bottom colour alpha | 0x202020.
3. **Untextured HUD quads** (12 §5.4, 10 §7): `Screen_FillRect3` quads (boss bar, markers, remaining bars, dialogue
   box) at the exact D3D coordinates (the port is 0.5 px off).

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Before numbers =
current master: same 7840193 (97.03 %), changed 221433, missing 18823, extra 4161309, reordered 37207. Report the
summary after plus the `-` (untextured) group line.
