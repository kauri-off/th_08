# IMPL60 — stage-clear frame, start rank state, EnemyMgr counter (audit A.37, A.38, A.39) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.37:

   | 37 | `gamemgr.rs:726` `stage_end` | 11 §4 п.1: в кадр клира loading := 1, score_display, затем return 3 | подтверждение проверяется сразу | S |

2. Audit row A.38:

   | 38 | `gamemgr.rs:379` | 11 §2: стартовое RANK_STATE (0, 0, 0, 0) | (16, 32, 0, 0) | H |

3. Audit row A.39:

   | 39 | `gamemgr.rs:1012` | 11 §2: 0x164D30C += 1 в начале `EnemyMgr_Calc`, вне диалога | +1 каждый игровой кадр, включая диалог | S |
