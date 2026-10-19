# RE-Q23 — spec consolidation (single source of truth)

Goal: the numbered specs `specs/00–16_*.md` + `specs/structs.md` become the only place an implementer needs to read.
Read `CLAUDE.md` (repo root) and the updated `docs/briefs/TASK_TEMPLATE.md` first.

## Deliverables

1. **Merge audit.** Go through every `specs/answers_*.md` (phase3 … impl21, bugs1/2, boss_phases). For each fact
   (behaviour, constant, order, condition, layout) check that the numbered spec states it, and is not contradicted by a later answer.
   Missing or stale → write it into the right numbered spec section (newest verified answer wins; note
   contradictions you resolve). Output `specs/changelog/AUDIT.md`: one row per answer section → target spec §, status
   (already there / added / corrected / obsolete).
2. **Move answers to a changelog.** Move the files with plain `mv` to
   `specs/changelog/` (same names) and update every reference in `specs/` and `docs/briefs/RE_WORKFLOW.md` to the new
   path. Spec text must read as a complete rule without opening the changelog; a changelog link is only evidence.
3. **Implementability pass on `specs/COVERAGE.md`.** Re-rate each feature by "can an implementer write it from the spec alone":
   COVERED / PARTIAL (list exactly what is missing: layout, timing, sprite ids, sounds, order) / MISSING. Include the alpha
   features explicitly: title/main menu, all stages, pause, continue, game over, result + name entry + score.dat,
   th08.cfg + options + key config, endings + staff roll, replay save/load, music room, spell practice. List the
   remaining INFERRED items per spec at the end.

Do not answer new questions in this task (IMPL22_QUESTIONS is the next task). Do not touch `src/`, do not run git.
Finish with: files changed, number of facts added/corrected, the PARTIAL/MISSING list.
