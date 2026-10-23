# IMPL83 — Vec3_FromPolar precision, laser and player box f32 edges (audit 86, 91, 93) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.3 (found by RE-Q30, `specs/changelog/answers_re_q30.md` §3). Implement from the
cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Where the
spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question.

## Deliverables

Needs wave 9 merged (`Player_LaserTest` from impl80).

1. **Audit 86** (05 §10): `Vec3_FromPolar` multiplies extended-precision cos / sin by r with one rounding to f32
   (use f64 cos / sin; no intermediate f32 rounding). Apply at every call site the spec names.
2. **Audit 91** (09 §6.1, 08 §6.3): laser collision goes through `Player_LaserTest` with f32 box edges.
3. **Audit 93** (08 §4 step 6, 09 §1.1): `Player_HitTest` / `HitTestNoBomb` / `GrazeTest` compare f32 box edges
   ((p − s/2) − 20 … s/2 + p + 20) with the player boxes +0x38C / +0x3A4.
