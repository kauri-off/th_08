# IMPL54 — bomb area test and +0xE2A7C timing, game-over bombs (audit A.22, A.23, A.26) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1 (line numbers there are from 85340f7 and may have moved).
For each row: read the cited spec section first, fix the code to the spec, remove the matching SPEC-GAP markers,
add a unit test where the behaviour is testable without game data. If the spec does not settle a detail, keep a
one-line `// SPEC-GAP:` and add a question; never guess from traces.

## Deliverables

1. Audit row A.22:

   | 22 | `bomb.rs:58` `Area::contains` | 09 §4.5: зона урона-круг — **точечный** тест по центру врага, `≤ r²` | расстояние от бокса врага, `< r²` | S |

2. Audit row A.23:

   | 23 | `bomb.rs:424` | 09 §1.1: +0xE2A7C держится до конца бомбы **включая кадр окончания**, сбрасывается следующим неудачным тестом старта | сбрасывается в кадр окончания (звезда / time orb дают не 100 на 1 кадр раньше) | S |

3. Audit row A.26:

   | 26 | `player.rs:1036` | 09 §6.2: при game over жизни и бомбы **не меняются** | бомбы сбрасываются в sht bombs | S |
