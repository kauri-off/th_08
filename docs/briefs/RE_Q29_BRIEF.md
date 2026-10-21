# RE-Q29 — replay frame hook vs traces, next divergences, open implementer questions

Read `docs/briefs/RE_WORKFLOW.md` first. Answers go into the numbered specs. The changelog
`specs/changelog/answers_re_q29.md` uses SPEC FIXED / CODE BUG / NEW FACT labels and ends with the CODE BUG list.
Never edit `src/`. Use a scratch port in `re/work/runs/q29/portfix/`, copied from the current `src/`, with an isolated
`XDG_CONFIG_HOME`.

## Questions

1. **11 §1.4 `Replay_FrameHook` 0x4522A0 contradicts every recorded trace.** The spec says the hook is linked at
   prio 7 always while recording and resets the RNG call counter (+4) every frame. In golden, fullrun_noclip and
   selftest1 the recorded `rng_ctr` never resets during gameplay (selftest1: 82 at game start, then 498, 914 … 7986).
   Open PR #29 (branch `claude/tender-cannon-4zx5tf`, `src/replay.rs`) implements the spec, and all three sessions
   then diverge on the game-start frame (rng_ctr 0x52 recorded vs 0 port).
   Find out:
   - when the hook node is really linked and run (registration path and gates);
   - what it writes (+0xD8, the counter, anything else).

   Also answer `docs/briefs/IMPL73_QUESTIONS.md` Q1–Q4: debug playback flag word; slow-mode counter and where gm+0x2D
   is cleared; OR-accumulation details. Fix 11 §1.4 / §4 / §7 and 15 §3.1.
2. **Next first divergences on master** (896927b): golden row 10782 (score 0x182AFF recorded vs 0x2DD323 port),
   fullrun_noclip 9408 (flags 0x10084 vs 0x10004, bit 7), demo 2 frame 4660, demo 3 frame 6682. For each:
   - find the root cause;
   - confirm the fix on the scratch port;
   - give the numbers after the fix.
3. Answer the still-open questions in `docs/briefs/IMPL35_QUESTIONS.md` … `IMPL40_QUESTIONS.md` in the numbered specs,
   skipping any that RE-Q27/Q28 already answered.
