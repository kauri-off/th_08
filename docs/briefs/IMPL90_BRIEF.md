# IMPL90 — remaining trig rounding sites, aura / op-128 update order (RE-Q31 CODE BUG 7–8) — local task

Source: `specs/changelog/answers_re_q31.md` §3 items 7–8. Implement from the cited numbered-spec sections only;
spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL90_QUESTIONS.md`.

## Deliverables

1. **Trig rounding** (05 §10 trig-site table; 07 ops 38 / 66 / 67 / 166, §8 mode 1, §10.3a; 14 Reimu orbs): match each
   listed site's rounding — `Vec3_FromPolar` (f32(f64 cos·r)) for enemy move mode 1 and the kill-children time orbs;
   f32(cos·r) single rounding for ops 38 / 166; op 66 / 67 delta = f32(f32(cos·spd)·dur) (not spd·dur first); Reimu
   bomb orbs f32(f32(sin·r) + cx). Sites the table lists as plain f32 cos / sin (laser draw / cancel, `Vec2_Rotate`
   boxes, effect burst / converge) stay as they are.
2. **Aura and op-128 effects** (07 §10.1 steps 4 and 7): the aura VM position is written in step 4 (each pass, before
   the screen check); the op-128 effect update runs in the step-7 tail after the boss marker (none after a boss
   mode-0/1 release).

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos).
