# Implementer task impl12 — answers to impl10/impl11 questions, spell plates and cut-ins

Read `docs/briefs/IMPL_TEMPLATE.md` first and follow it. Then docs (README → STATUS → DECISIONS → FORMATS) and the specs
below. Deliverables (ONLY these three; finish and verify one before the next):

1. `specs/answers_impl10.md` — apply every answer (Q1–9) and the spec sections it cites; remove the SPEC-GAPs it closes.
2. `specs/answers_impl11.md` — apply every answer (Q1–14): bomb tint lifetime (0x4EA49C flag, enemies prio 8, flying
   player bullets, one frame after the bomb), +0x3D no-spark writers, chain-kill ÷3 compounding, dissolve-spell trigger
   and end flash, option/bomb quirks; remove the SPEC-GAPs it closes.
3. `specs/12_menus_hud.md` §5.8 — boss and player spell-name plates, cut-ins, boss streak backgrounds, the "Bonus /
   history" line (with the quirks listed there).
Verify with screenshots (compare with `specs/data/ref/spell54_*.png`), the full scripted 1→6 run still finishing,
`cargo test --release` with TH08_DIR, and the wasm check. Put new questions in `docs/briefs/IMPL12_QUESTIONS.md`.
