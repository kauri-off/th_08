# RE: answers to IMPL18 + IMPL19 questions (gameplay sync blockers)

Deliverables:
1. `specs/answers_impl18.md`: every question in `docs/briefs/IMPL18_QUESTIONS.md` (golden frame 1451 Yukari option target selection, selftest1 frame 712 item drop mode during a bomb / +0xFDC, the smaller visual items). Verify at runtime with the probe on the recorded sessions (`play_session.sh`) where possible.
2. `specs/answers_impl19.md`: every question in `docs/briefs/IMPL19_QUESTIONS.md` (full-power checksum draws, off-screen enemy removal box, extra bullets in demo 2 frame 2261 / demo 3 frame 1501, loading "+6").
3. Fix the specs in place; list changed sections at the top of each answers file. Do not replay `fullrun_noclip` in full (too long); short partial replays are fine.
