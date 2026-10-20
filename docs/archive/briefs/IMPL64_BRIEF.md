# IMPL64 — options volume steps, title music after scene 5, resulttext slot (audit A.53, A.54, A.59) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.53:

   | 53 | `menu.rs:653` | 15 §1.3: громкость ±4 по фронту, затем ±1 (фронт или счётчик > 29); превью SE 0x1D раз в 50 кадров | ±1 / ±4 на повторе, без превью | U |

2. Audit row A.54:

   | 54 | `menu.rs:785` | 00 §3.2: титульная музыка не перезапускается после сцены 5 | всегда | V |

3. Audit row A.59:

   | 59 | `menulist.rs:14` | 00 §3.2: resulttext.anm → слот 22 | 21 | H |
