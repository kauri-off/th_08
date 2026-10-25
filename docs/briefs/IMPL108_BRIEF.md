# IMPL108 — bomb tint-off, death silhouette, text rendering pipeline (RE-Q38, RE-Q36, RE-Q41) — local task

Sources: `specs/changelog/answers_re_q38.md` (IMPL103 Q1 row, "Player_Die white silhouette"),
`answers_re_q36.md` (text.rs:2 row), `answers_re_q41.md` (text.rs:196 row). Implement from the cited numbered-spec
sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details:
one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL108_QUESTIONS.md`.

## Deliverables

1. **Bomb tint** (09 §7, 06 §10.2): a normal-mode bomb start does VM bit 17 off, ring ended, bit 10 off, then
   `AnmMgr_TintOff`, then the index; no tint-off at the bomb end; `Player_DyingUpdate` turns it off only at the real
   death, not on every dying frame. Close the bomb.rs marker.
2. **Death silhouette** (09 §6.1): `Player_Die` white silhouette (colour2 + VM flag bit 17).
3. **Text pipeline** (10 §6): fresh A1R5G5B5 surface, 1-bit alpha, 5-bit colour, the vertical colour gradient on opaque
   pixels; then the exact 2:1 D3DX TRIANGLE downsample into A4R4G4B4 (weights 1/16, 7/16, 7/16, 1/16 per axis, edge
   wrap, unweighted channels, f32 sums in source order, trunc(x·15 + 0.5)). Glyph shapes stay platform (text.rs:2 stays
   as the only marker there). Close text.rs:196. Native and web paths both.

All sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3) — logic must not change; report
the golden draw comparison before/after (now 8070147 same quads, 18 extra). Report the SPEC-GAP count (was 48).
