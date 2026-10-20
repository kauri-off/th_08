# IMPL46 — stale SPEC-GAP markers (audit §C) — cloud task, no behaviour change

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §C (21 markers whose question the numbered specs now answer).

## Deliverables

1. For every row of audit §C where "код уже соответствует" (the port already matches): read the cited spec section;
   if it confirms the port, replace the `// SPEC-GAP:` with a short normal comment citing the § (per `CLAUDE.md`),
   or delete it if the code is obvious. If the spec does NOT confirm the port, leave the marker and add a question.
2. Rows that point at a divergence (`task.rs:110` → audit D.1, `bomb.rs:421` → audit A.23): rewrite the marker so it
   states the spec § and the remaining difference in one line; do not change the code.
3. No change to any code path: the diff must touch comments only. State this in the PR and give
   `grep -r SPEC-GAP src | wc -l` before → after (expected 168 → ~147).
