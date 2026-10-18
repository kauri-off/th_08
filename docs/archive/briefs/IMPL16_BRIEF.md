# impl16: demo sync push (answers_impl14)

Input: `specs/answers_impl14.md` (answers to IMPL14_QUESTIONS) and the spec sections it lists as fixed
(07 §10.x, 08 §4.3a, 09 §1.1, 11 §3.4/§4, 13 §2.6, 14 §3, 15 §2.9/§2.10/§3.4).

Deliverables:
1. Implement every answer: effect 38 spawn from the player-mode reaction for op-83 children (and the other effect types
   13 §2.6 lists as drawing RNG at spawn), the start-of-update bullet counter (spawn limit / slow mode use it),
   time-orb drop on kills at gauge max, ±200 gauge rule from the focus byte, demo music fade 3.0 s, play-stat counting,
   option free at t > 16, VRSM constants for a fresh score.dat. Remove the SPEC-GAPs these close.
2. Push demo sync with `cargo run --release --bin demosync`: after each fix find the next first divergence; fix it when
   the specs cover it, otherwise write a precise question (frame, field, port vs trace values, RNG call-site list from
   the demosync tool) into `docs/briefs/IMPL16_QUESTIONS.md` and move on to the next demo.
3. Raise the thresholds in `MIN_SYNC` (src/demosync.rs) and `DEMO` (src/drawlog.rs) to the new levels; report per-demo
   sync frames before/after and the draw-log match percentages.
