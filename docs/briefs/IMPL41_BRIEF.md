# IMPL41 — `drawview`: interactive overlay of two draw logs (port tooling)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Port tooling, no spec section, no game behaviour change.

The session report (`src/drawreport.rs`, `index.html`) shows a few frames as reference / port / diff PNGs. The user
wants the same comparison for **whole recordings**: play two draw logs on top of each other and scrub through them.

## Deliverables

1. **Loading and alignment** (`src/bin/drawview.rs` + library code next to `drawreport.rs`/`drawlog.rs`).
   - CLI (clap): `drawview <A> <B> [--from N] [--to N] [--playfield]`. A and B are draw logs in any form the reader
     already accepts: a session dir (`draw_*.drawlog.xz` chunks), a single `.drawlog[.xz]`, a session tool output dir
     (`draw.drawlog.xz`). Typical use: `drawview sessions/golden target/golden_report`.
   - Align frames the same way the session report does (scene key with visits, demo key, present numbers); show
     unmatched frames as "missing" instead of shifting everything.
   - Render both through the existing draw-log `Renderer` (offscreen wgpu). The renderer keeps a persistent buffer, so
     seeking backwards must restart from a safe point (e.g. chunk start / last full clear); cache rendered frames
     (bounded memory) so scrubbing and stepping back a few frames is instant. Decode/render ahead on a worker
     thread so playback holds 60 fps where possible.
2. **Viewer window (egui on wgpu/winit, as in the launcher).**
   - Modes: A only, B only, side by side, **overlay** (B over A with an opacity slider), **diff** (the same red-pixel
     rule as `diff_image`, threshold adjustable), flicker (alternate A/B every N frames).
   - Timeline slider, play/pause, speed (0.25×–8×), step ±1 frame (arrow keys), jump to frame number, zoom 1×–3×,
     playfield-only crop.
   - Status line: frame/present numbers of A and B, scene, game frame, differing-pixel %.
3. **Finding differences.**
   - A diff-% strip under the timeline (computed in the background as frames are rendered; colour per frame).
   - "Next / previous differing frame" (threshold on diff %), and "first divergence".
   - Save the current view as PNG (A, B, diff, overlay) under a chosen dir.
   - Short README section ("Comparing recordings") and `docs/STATUS.md` entry.

## Verification

- Game metrics untouched (no game code change expected; if shared code changes, rerun golden/fullrun/selftest/tests).
- `cargo fmt --check`, 0 warnings, wasm check (the tool is native-only).
- Smoke: open `sessions/golden` vs a fresh `session` output on golden; render screenshots of each mode offscreen or
  through the tool's PNG export into `target/impl-work/impl41/` for review. Never take full-desktop screenshots.
- Work files under `target/impl-work/impl41/`.
