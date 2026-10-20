# IMPL65 — spell-practice difficulty and shot change, menu same-frame transitions (audit A.56, A.57, A.58) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.56:

   | 56 | `menulist.rs:1007` | 16 §6.2: difficulty = `Spell_DifficultyOf(id)` (Last Words → 1) | CATK +0x0F | U |

2. Audit row A.57:

   | 57 | `menulist.rs:557`, `:571` | 16 §6.1: смена шота обнуляет +0x1442C; Bomb пишет строку в g_StageIdx | нет | U |

3. Audit row A.58:

   | 58 | `menulist.rs:436`, `:594`, `:1023`, `:1169`, `:1176` | 12 §2 (RE-Q25): переходы «return 2» (9/15 → 11/16, 11 → 9, 16 → 17, 17 → 16) идут в том же кадре через повторный вызов узла, и `RunRange` + VM описания отрабатывают в этом кадре **дважды**; путь назад из practice — по экрану на кадр; лаг строки replay — по 15 §3.8 | итог «в кадр нажатия» совпадает, но сделан частными случаями по логу mopup1 (трассы как источник поведения запрещены `CLAUDE.md`); двойного прогона VM нет; задержка 30 кадров и строка 0 → snap взяты из лога | U |
