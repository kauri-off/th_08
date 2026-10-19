# IMPL19: apply answers_impl16 / answers_impl17 (gameplay)

Deliverables:
1. Apply everything in `specs/answers_impl16.md` not yet in the port (impl18 already did the per-enemy accumulator and the item state 3→1 rule): every-third counter and drop-table index set by `Rng_Range16(3)` / `Rng_Range16(8)` at each stage load (check before increment), op 66 mirror negating delta.x, anything else listed there. Remove the SPEC-GAPs these answers resolve.
2. Apply the Q2/Q5 part of `specs/answers_impl17.md`: minimum loading 31 frames (81 replay) for demos/replays, depth-clear rule, stg4abg ribbon colours, night clock tied to stage-title VM 0, the replay fps text "%2d" at (384, 448) colour 0xFFFFFFD0 (pick a fixed refresh rule and note it).
3. Re-measure: demo sync (`MIN_SYNC`), demo draw thresholds, `session_sync` (golden/selftest1 leading rows), menu thresholds; raise thresholds to the new values (never lower one without stating why). Put questions in `docs/briefs/IMPL19_QUESTIONS.md`.
