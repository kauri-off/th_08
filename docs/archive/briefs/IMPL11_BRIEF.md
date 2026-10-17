# Implementer task impl11 — bombs, options/laser/shot drawing

Read `docs/briefs/IMPL_TEMPLATE.md` first and follow it. Then docs (README → STATUS → DECISIONS → FORMATS) and the specs
below. Deliverables (ONLY these two; finish and verify one before the next):

1. Bombs — `specs/14_bombs_options.md` §1–2: bomb objects, `Bomb_Start`, background tint, all 16 bombs
   (8 normal + 8 Last Spell) and the dissolve spell, with damage, bullet cancel, invulnerability, SE and effect
   hooks (sound.rs / effect.rs exist now; hit sparks from bomb damage areas per specs/answers_impl9.md §1). Replace any existing bomb stub.
2. Options, player laser, shot drawing — 14 §3–6: familiars (Yukari, Remilia solo, Youmu's half / solo), Alice's
   focused laser, shot draw / red tint / hitbox marker, and the corrections to 09 in §6.
Verify with screenshots of each bomb (TH08_SHOT + scripted input; use a debug env var to force bomb/character if
needed), the full scripted 1→6 run still finishing, `cargo test --release` with TH08_DIR, and the wasm check.
Put new questions in `docs/briefs/IMPL11_QUESTIONS.md`.
