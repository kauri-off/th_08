# Implementer task impl10 — bombs, options/laser/shot drawing, Phase 5 fixes

Read `specs/IMPL_TEMPLATE.md` first and follow it. Then docs (README → STATUS → DECISIONS → FORMATS) and the specs
below. Deliverables (ONLY these three; finish and verify one before the next):

1. Bombs — `specs/opus/14_bombs_options.md` §1–2: bomb objects, `Bomb_Start`, background tint, all 16 bombs
   (8 normal + 8 Last Spell) and the dissolve spell, with damage, bullet cancel, invulnerability, SE and effect
   hooks (sound.rs / effect.rs exist now). Replace any existing bomb stub.
2. Options, player laser, shot drawing — 14 §3–6: familiars (Yukari, Remilia solo, Youmu's half / solo), Alice's
   focused laser, shot draw / red tint / hitbox marker, and the corrections to 09 in §6.
3. Phase 5 fixes — `specs/opus/answers_phase5.md`: apply every answer to existing code (ANM VM, ECL, bullets/items,
   player, msg/flow/hud) and resolve the matching `// SPEC-GAP` lines; note any answer you could not apply.

Verify with screenshots of each bomb (TH08_SHOT + scripted input; use a debug env var to force bomb/character if
needed), the full scripted 1→6 run still finishing, `cargo test --release` with TH08_DIR, and the wasm check.
Put new questions in `specs/IMPL10_QUESTIONS.md`.
