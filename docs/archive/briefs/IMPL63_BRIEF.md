# IMPL63 — score.dat stage byte, replay score field, replay spell-practice flags (audit A.46, A.48, A.49) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.46:

   | 46 | `scoredat.rs:67` | 15 §2.3 / 16 §2.3: стандартный stage byte = 0, отображение через таблицу 0x4C7F80; magic "DMYS" | stage byte 1 | U |

2. Audit row A.48:

   | 48 | `replay.rs:350` | 15 §3.2: +0 := score только у **самой старшей** существующей записи | перезаписываются все | U |

3. Audit row A.49:

   | 49 | `replay.rs:415` | 15 §3.8: при воспроизведении spell practice — только биты 3 и 14 | добавляется bit 0 | U |
