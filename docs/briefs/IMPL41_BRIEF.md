# IMPL41 — `drawvideo`: comparison video of two draw logs (port tooling)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Port tooling, no spec section, no game behaviour change.

The session report (`src/drawreport.rs`, `index.html`) shows only ~9 frames as reference / port / diff PNGs. The user
wants the same comparison as a **video of the whole recording** (or a range): original and port overlaid / side by
side with the diff, frame by frame.

## Deliverables

1. **Frame source and alignment** (library code next to `drawreport.rs` / `drawlog.rs`).
   - Inputs A and B in any form the reader accepts: a session dir (`draw_*.drawlog.xz` chunks), a single
     `.drawlog[.xz]`, a `session` tool output dir (`draw.drawlog.xz`).
   - Align frames the same way the session report does (scene key with visits, demo key, present numbers). Unmatched
     frames render as a "missing" panel instead of shifting the rest.
   - Render both streams through the existing draw-log `Renderer` (offscreen wgpu), streaming: no full-run frame
     storage in memory or on disk.
2. **`src/bin/drawvideo.rs` (clap CLI, native only).**
   - `drawvideo <A> <B> -o out.mp4 [--from N] [--to N] [--mode MODE] [--playfield] [--scale K] [--fps F]`.
   - Modes: `triple` (default: A | B | diff side by side), `overlay` (B over A at `--alpha`, default 0.5),
     `diff` (the same red-pixel rule as `diff_image`, `--threshold`), `flicker` (alternate A/B every `--flicker N`
     frames), `split` (A and B side by side without diff).
   - Caption on every frame: present numbers of A and B, scene, game frame, differing-pixel %, and a marker on the
     first diverging frame.
   - Encoding with crates, not an external `ffmpeg` process (project rule: crates over hand-rolled / external tools):
     e.g. `openh264` (bundled source) + an MP4 muxer crate, or another crate pair that yields a file every normal
     player opens. If no crate route is practical, stop and report why before choosing anything else.
   - Progress output and a summary at the end (frames, missing frames, mean / max diff %, first divergence).
3. **Integration and docs.**
   - Optional `--video` flag on the `session` tool that writes `DIR/compare.mp4` (triple mode) next to `index.html`.
   - README section "Comparing recordings" with the golden and fullrun_noclip commands (fullrun's reference draw log
     lives in `re/work/runs/q26/fullrun_dl/`; wrap it with symlinks in `target/`, never write into
     `sessions/fullrun_noclip`). `docs/STATUS.md` entry.

## Verification

- Game metrics untouched (no game code change expected; if shared code changes, rerun golden/fullrun/selftest/tests).
- `cargo fmt --check`, 0 warnings, wasm check (the tool is native-only), Windows gnu check still passes.
- Smoke: golden reference vs a fresh `session` output on golden, a ~2-minute range in every mode, into
  `target/impl-work/impl41/`; report encode speed (frames/s), file size, and check the files with `ffprobe` (check
  only). Extract a few frames as PNG for review. Never take full-desktop screenshots.
- Work files under `target/impl-work/impl41/`.
