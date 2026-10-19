# IMPL21: apply answers_impl18 / answers_impl19

Deliverables:
1. Apply `specs/answers_impl18.md`: aimed-enemy pointer lifetime (set before the death check, not cleared by a mode-0 death, cleared by the enemy loop when the slot is empty; Yukari option sees it on the next player update), hit-by-bomb flag rule for drop mode, draw-list linking for timeline vs enemy-spawned enemies, bomb gauge on the end frame, character-select cursor, menu description fade-in on the loader release frame, title/nowloading draw order. Close the SPEC-GAPs these answer.
2. Apply `specs/answers_impl19.md`: full-power clamp as a checksummed write on every full-power collect (close the guess SPEC-GAP), off-screen removal box (check against what impl20 did), loading floor note. Use the saved original bullet dump for demo 2 frame 2261 if it helps.
3. Re-measure golden/selftest1/fullrun_noclip `session_sync`, demo `MIN_SYNC`, demo draw %, menus; raise thresholds (never lower without stating why). Questions to `docs/briefs/IMPL21_QUESTIONS.md`.
