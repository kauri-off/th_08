# IMPL58 — pshot hit sequence order (audit A.32) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.32:

   | 32 | `pshot.rs:840` | 09 §4.5: точный порядок (rot → SetScript без обнуления pos → rot → Effect 5 → z 0.1 → state 2), флаг 0x2000 не ставится повторно | эффект до рестарта VM, pos и 0x2000 переставляются | S |
