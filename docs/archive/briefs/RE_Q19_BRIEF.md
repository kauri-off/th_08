# RE: boss phase transitions + remaining IMPL19 Q3

Deliverables:
1. Boss phase changes (user report: the port's phase 1 → 2 transition is broken). Check the specs (07 ECL boss/spell ops, life/timer thresholds, interrupt/sub switching, bullet clear, spell start, boss invulnerability between phases) against the binary and at runtime: replay the start of `fullrun_noclip` through the stage 1 boss (stage 2 loads at poll 11269; do not replay further) and log the boss's ECL sub, life, timers and phase changes frame by frame into `specs/data/q19/`. Write the exact transition sequence (which frame does what) to `specs/answers_boss_phases.md`; fix the specs.
2. IMPL19 Q3 remainder: why the 4 chained child enemies in demo 3 frame 1501 do not fire, and what the 2 extra port bullets at demo 2 frame 2261 are (diff the saved original bullet dump; describe the rule, not port code). Append to `specs/answers_impl19.md`.
3. List changed spec sections at the top of each answers file.
