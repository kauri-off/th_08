# IMPL52 — enemy trail ring and draw, op 176 (audit A.17, A.18) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.17:

   | 17 | `enemy.rs:1137` `screen_check`, `enemy.rs:2275` `draw_layer` | 07 §10.1 п.4: кольцо трейла 96×0x1C (сдвиг на каждом проходе), враг с трейлом освобождается, только когда и он, и самый старый след вне экрана; 07 §10.6: отрисовка трейла | кольца нет; тест старейшего следа пропущен; трейл не рисуется (op 157: 22 использования, n = 15/90) | S |

2. Audit row A.18:

   | 18 | `eclvm.rs` op 176 | 07 §7: при bit 13 и живом boss 0 — `Player_DamageAgainst` по всему полю каждый кадр (все выстрелы считаются попаданиями) | помечено «Not implemented» | S |
