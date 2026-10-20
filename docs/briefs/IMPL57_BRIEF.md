# IMPL57 — pshot animation test, option position, laser bit 13 (audit A.29, A.30, A.31) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.29:

   | 29 | `pshot.rs:250` | 14 §3.1: тест анимации идёт после теста атаки всегда | только при старте sub 0 | S |

2. Audit row A.30:

   | 30 | `pshot.rs:428` `origin_pos` | 09 §4.3: позиция опции читается без проверки занятости слота | у свободной опции берётся позиция игрока | S |

3. Audit row A.31:

   | 31 | `pshot.rs:555`, `:667` | 14 §4: обе лазерные функции проверяют GameFlags bit 13 | не проверяется | S |
