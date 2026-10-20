# IMPL50 — ECL kill-all self test, native 31, op 181 (audit A.12, A.15, A.16) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.12:

   | 12 | `eclvm.rs:1656` op 95; `eclvm.rs:1736` op 123 (KillAll); `enemy.rs:1778` `kill_non_bosses` | 07 §7 op 95, §10.2 (RE-Q24): **проверки на себя нет**; вызывающий не-босс без B bit 6 тоже получает life 0 и прыгает в свой death sub | вызывающий исключается (`except`) | S |

2. Audit row A.15:

   | 15 | `eclvm.rs:1083` native 31 | 07 §12: тип 3 (бомба), если игрок бомбит в момент вызова, иначе 5 | всегда 5 | S |

3. Audit row A.16:

   | 16 | `eclvm.rs:2034` op 181 | 07 §7: при clock ≥ 12 ничего, **даже без звука** | звук 0x2D всегда | V |
