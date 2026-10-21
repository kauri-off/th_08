# IMPL53 — ECL natives 26/28/29, Spell_End bomb cooldown (audit A.19, A.21) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.19:

   | 19 | `eclvm.rs:1018` native 26; `:1074` natives 28/29 | 07 §12: прерывания stage VM; масштаб скоростей пуль и спрайты 0x60–0x6F → 0x6F | только game speed / таймер | S |

2. Audit row A.21:

   | 21 | `player.rs:399`, `enemy.rs:1464` `finish_spell` | 07 §11.1, 09 §1.1: `Spell_End` ставит кулдаун бомбы +0xE2A6C := 16 (единственный писатель) | поле никто не пишет, кулдаун всегда 0 | S |
