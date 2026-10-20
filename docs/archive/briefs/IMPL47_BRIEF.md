# IMPL47 — score file and name entry (audit A.45, A.60, A.61) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1. Fix the code to the spec; remove the matching SPEC-GAP markers.

## Deliverables

1. **A.45** `scoredat.rs` `insert_hscr` (15 §2): a new entry goes before equal scores (`>` count, not `>=`).
   Unit test with two equal scores.
2. **A.60** `result.rs` name entry input (16 §2.2): Up, Down, Left, Right are four independent tests per frame,
   in the spec's order (no "Up wins over Down"). Unit test with Up+Down held.
3. **A.61** `supervisor.rs` date written with a score (16 §2.2): local time, not UTC. Use a crate (`chrono` or
   `time` with local offset); keep the wasm build compiling (use the JS local date there if the crate needs it).
