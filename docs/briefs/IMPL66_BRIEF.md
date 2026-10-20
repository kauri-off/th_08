# IMPL66 — face files, ending presents and start values, score.dat tie order (audit A.62, A.63, A.64, A.67) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.62:

   | 62 | `msg.rs:31` | 10 §3: потабличные имена face-файлов; в spell practice лица игрока не грузятся, cut-in `…sp` по id карты | имена собраны из диапазона | V |

2. Audit row A.63:

   | 63 | `ending.rs:135` | 16 §1.2 п.1: сброс кэшей AnmManager + два лишних Present с очисткой в белый | не сделано (сдвигает нумерацию Present) | U |

3. Audit row A.64:

   | 64 | `ending.rs:123`, `:191` | 16 §1.2: начальный цвет 0; +0x2A94 стартует с 0 и не ставится в LoadScript | 0xFFFFFF; ставятся оба | H |

4. Audit row A.67:

   | 67 | `scoredat.rs` `ranking` (impl47 Q1) | 15 §2.3: score.dat перечитывается в каждом `Result_OnRegister` (режимы 0, 1, 2), записи вставляются `ScoreList_Insert`, так что равные очки меняют порядок при каждой загрузке | файл читается один раз, порядок равных сохраняется | U |
