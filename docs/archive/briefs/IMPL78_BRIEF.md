# IMPL78 — blue square boss effect never fades (user-reported) — local task

Read `CLAUDE.md` and `docs/briefs/IMPL_TEMPLATE.md`. Specs `specs/00–16_*.md` + `specs/structs.md` are the only
source of behaviour; draw logs only locate the divergence.

## Symptom

During boss fights, blue square sprites drift away from the boss, never disappear, and leave the playfield.

## Evidence (draw logs, format `specs/data/drawlog/FORMAT.md`)

The sprite: texture `etama.anm#1`, uv (0.625, 0.875)–(0.6875, 0.9375) = pixels (160,224)–(176,240), colour
xx6060d0, z 0.9994.

- **Original, golden, stage 2 boss.** Reference log `sessions/golden/draw_00013.drawlog.xz`, presents 24000–25200.
  There are always 6 of these quads around the boss, each with a different alpha (0x43…0xdb): they appear, rotate,
  fade and are replaced. Example present 24728: centres ≈ (212,148), (237,60), (70,110), (135,56), (190,117).
- **Port, same session.** `cargo run --release --bin session -- specs/data/sessions/golden --out /tmp/g` writes
  `/tmp/g/draw.drawlog.xz`. The port draws **none** of these quads in that range. Golden's logic trace matches the
  original fully, so this is a draw-only object (effect / ANM side), not gameplay.
- **Port, fullrun_noclip, final-stage boss phase 1.**
  `session specs/data/sessions/fullrun_noclip --out /tmp/f --port-drawlog --from 112700 --to 115300` (≈5 min). The
  port draws 1–6 of these quads. They move steadily outward, (224,143) → (418,65) / (249,20) / (23,91) …, and never
  fade.

## Deliverables

1. Find which object draws this sprite (effect type, ANM script) and what the spec says about its spawn, motion,
   fade and removal. Fix the port to match.
2. Verify:
   - in the golden port log, presents 24000–25200 hold the same count of these quads as the reference, at roughly
     the same positions;
   - in fullrun none leaves the playfield without fading.

   Report the counts.
3. Usual checks: `cargo fmt --check`; 0 warnings; wasm `cargo check --release --lib --target wasm32-unknown-unknown`;
   `cargo test --release`. Golden must stay a full match (25634), fullrun ≥ 29947, demos in sync.

If the spec does not explain the behaviour: `// SPEC-GAP:` plus a question in `docs/briefs/IMPL78_QUESTIONS.md`.
