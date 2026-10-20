# IMPL62 — effect removal rules, ring segments, list C billboard (audit A.41, A.42, A.43) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.41:

   | 41 | `effect.rs:1338`, `:1420` | 13 §3: type 1 и type 2 удаляются при 0x18B8A2C ≠ 0; type 7 удаляется при 0x164D2C8 < 2; заморозка — по bit 10 / freeze byte | этих правил нет | S |

2. Audit row A.42:

   | 42 | `effect.rs:450` | 13 §2.6: кольцо по умолчанию **24** сегмента (кроме перечисленных переопределений) | 32 | V |

3. Audit row A.43:

   | 43 | `effect.rs:840` | 13 §2.4: список C — `DrawBillboard` через `Camera_Set2D` на вьюпорте поля | 2D-спрайт в pos | V |
