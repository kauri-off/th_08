# Implementer task impl10 — visual bug fixes from answers_impl9, Phase 5 fixes

Read `docs/briefs/IMPL_TEMPLATE.md` first and follow it. Then docs (README → STATUS → DECISIONS → FORMATS) and the specs
below. Deliverables (ONLY these three; finish and verify one before the next):

1. Priority bugs — `specs/answers_impl9.md` §1–3 (and the corrected parts of `specs/13_sfx_effects.md`):
   - Hit spark (effect type 3): player bullets hitting enemies must NOT spawn it (bullets only spawn type 5).
     It comes only from bomb/last-spell damage areas with the every-4th-hit rule; bombs are not implemented yet,
     so implement the rule at the damage-area hook so impl11 can use it. Keep the RNG draw count exact.
   - Ring texture mapping (spell-card ring, death ring, every ring user): long sprite axis along the ring, short axis
     across the band, wrapping addressing, repeat count from the sprite span; radius/width/easing as specified.
2. All other answers in `specs/answers_impl9.md` (§4–18: particles 19/51/63, op 128 orbit effect, natives 3/6/20,
   background list + effect level, auras, stage sparkles, shake consumers, popup colours/glyphs, title description
   text, …). Resolve the matching `// SPEC-GAP` lines.
3. Phase 5 fixes — `specs/answers_phase5.md`: apply every answer to existing code (ANM VM, ECL, bullets/items,
   player, msg/flow/hud) and resolve the matching `// SPEC-GAP` lines; note any answer you could not apply.

Verify: screenshots of a boss under fire (no spark stream), the spell-card ring at several frames (repeating text
around the ring) and the death ring; the full scripted 1→6 run still finishing; `cargo test --release` with TH08_DIR;
the wasm check. Report the SPEC-GAP count before/after (79 now). Put new questions in `docs/briefs/IMPL10_QUESTIONS.md`.
