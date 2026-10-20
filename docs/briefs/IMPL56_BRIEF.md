# IMPL56 — player start z, dead box_in_cancel_area, forced-start cooldown (audit A.28, A.33, A.68) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.28:

   | 28 | `player.rs:36` | 09 §6.4: старт (192, 384, **0.49**) | z 0.0 | H |

2. Audit row A.33:

   | 33 | `player.rs:791` `box_in_cancel_area` | 09 §8 (RE-Q24): аналога в оригинале нет | мёртвый код портa | H |

3. Audit row A.68:

   | 68 | `player.rs` декремент +0xE2A6C (impl46 Q2) | 09 §1.1: декремент пропускается при forced-старте (+6 set и +0xE2A68 == 1) | декремент всегда | S |
