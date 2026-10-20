# IMPL59 — stage step bit 10, spell-practice condition, sparkle z test (audit A.34, A.35, A.36) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.34:

   | 34 | `stage.rs:600` `step` | 06 §5: ранний return при GameFlags bit 10 | нет | S |

2. Audit row A.35:

   | 35 | `stage.rs:654` | 06 §5: в spell practice вместо условия frame > 699 | не проверяется | V |

3. Audit row A.36:

   | 36 | `stage.rs:895` | 06 §11.1: точки блёсток только при 0 ≤ z ≤ 1 | проверка отсутствует | V |
