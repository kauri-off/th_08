# IMPL51 — spawn_child order, chain link position, spawn_prepare positions (audit A.14, A.66, A.13) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.14:

   | 14 | `eclvm.rs:629` `spawn_child` | 07 §10.5: бит 8, бит 11, layer, contact off и аура — **после** spawn-time `Ecl_Run`; ссылка цепочки пишется последней; aura VM bit 17 := A bit 2; aura +0x14 негируется при e+0x2E0C bit 0 | всё, кроме contact off, ставится до прогона; две последние детали не сделаны | S |

2. Audit row A.66:

   | 66 | `eclvm.rs` `spawn_child` (impl42 note) | 07 §10.5: новый ребёнок цепочки встаёт сразу после породившего | ставится в конец цепочки | S |

3. Audit row A.13:

   | 13 | `enemy.rs:901` `spawn_prepare` | 07 §4.1: prev_pos и final_pos остаются (0,0,0) из шаблона, первое смещение (vars 10085–87) равно позиции спавна | ставит обе в позицию спавна | H |
