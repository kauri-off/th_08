# IMPL61 — human rate place, register order and BGM slots, config 60 bytes (audit A.40, A.44, A.47) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.40:

   | 40 | `player.rs:1186` | 15 §2.3: human-rate — в `EnemyMgr_Calc`, только при таймере менеджера > 15 | считается в player, без условия | U |

2. Audit row A.44:

   | 44 | `gamemgr.rs:677`, `:695` | 11 §3.1: Effects регистрируются до HUD; загружаются BGM-слоты 0 и 1/2, играет 0 | HUD первым; грузится только слот 0 | H |

3. Audit row A.47:

   | 47 | `config.rs:115` `apply_gameplay` | 11 §3.4: копируются все 60 байт, без клампа | только 3 поля, кламп эффектов | S |
