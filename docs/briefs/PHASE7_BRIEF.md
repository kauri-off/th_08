# RE phase 7 — coverage audit (dirty room)

Goal: make sure the specs cover the whole game, so the port can be completed without guessing.

Deliverables (max 3):

1. `specs/COVERAGE.md` — map of the whole game to specs. Use `re/symbols.csv`, `re/extracted/callgraph.tsv`, the scene/task lists and the data files. For every subsystem/feature (scenes, menus incl. pause/continue/practice/spell practice/replay menu, Extra stage, story team switching, time orb / youkai gauge / human-youkai mechanics, familiars, dialogue, endings, staff roll, music room, result screen, cfg, score, replays, demo/attract mode, input, sound, fps/skip, screenshots…) give: spec file + section, status (COVERED / PARTIAL / MISSING), and the main function addresses. Also list large unnamed function clusters reachable from the game loop that no spec covers.
2. Close the open INFERRED items from phase 6 where possible (fps flag 0x17CEA90, Supervisor+0x1A4 bit 3, CLRD+0x20, info panel +0x69, byte 0x164D0B2, cfg +0x26, ending fade quad colour, natives 3/6/20 intent): check struct-base writes, not only direct addresses. Fix specs in place; summarise in `specs/answers_phase7.md`.
3. In `re/NOTES.md`, a ranked list of the next RE briefs (each ≤3 deliverables) that would bring every PARTIAL/MISSING item to COVERED.

Follow `docs/briefs/TASK_TEMPLATE.md` and `docs/briefs/RE_WORKFLOW.md`.
