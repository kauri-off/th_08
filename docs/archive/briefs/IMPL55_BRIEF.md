# IMPL55 — player freeze byte, +0xE2A9C reset, spell-practice invuln timers (audit A.24, A.25, A.27) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.24:

   | 24 | `player.rs:1143` `frame` | 09 §1 п.1: freeze byte 0x160F534 → аурам флаг 0x80000, return | не сделано | S |

2. Audit row A.25:

   | 25 | `player.rs:897` | 09 §3: сброс +0xE2A9C только для команд | делается и для соло | S |

3. Audit row A.27:

   | 27 | `player.rs:1088`, `player.rs:568` | 09 §6.3 / §6.4: в spell practice (bit 14) таймер неуязвимости не ставится (остаётся 30); стартовый таймер 10, не 120 | 240 / 120 всегда | S |
