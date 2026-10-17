# Implementer task impl13 — visual bugs round 2

Read `docs/briefs/IMPL_TEMPLATE.md` first and follow it. Then `docs/bugs/VISUAL_BUGS_2.md` and `specs/answers_bugs2.md`.
Deliverables (ONLY these three; finish and verify one before the next):

1. C1 menu seam: fix the sampling issue per 05 §12.4 / 12 §2.2 (compare with `specs/data/ref/c1_menu_practice_sel.png`).
   Keep the fix general (all 2D sprite draws), not menu-only, unless the spec says otherwise.
2. C2 character select: difficulty plate (interrupt 9, slide to (16, 384)) and the FinalB / clear notice (12 §2.4);
   compare with `specs/data/ref/c2_*.png`.
3. C3 gauge readout (12 §5.9), and check the death/drop star sparks (13 §3, effect type 4) and time orbs against
   `specs/data/ref/c3_*.png`.
Verify with screenshots, the full scripted 1→6 run, `cargo test --release` with TH08_DIR and the wasm check.
Put new questions in `docs/briefs/IMPL13_QUESTIONS.md`.
