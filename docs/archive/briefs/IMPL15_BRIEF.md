# impl15: port-side draw log + automatic comparison with the original

Reference data (from the original, recorded by the dirty room): `specs/data/drawlog/` — read `FORMAT.md` and `README.md` first.
Menu logs/screenshots are in git; demo chunks `demos/*.drawlog.xz` exist locally only (tests must skip cleanly if missing).

Deliverables:
1. Port draw log: `TH08_DRAWLOG=<path>[,from-to]` writes, per presented frame, every quad in draw order in exactly the
   FORMAT.md format (texture label, screen-space vertices, UVs, colour, blend/alpha-test/depth/fog state, viewport,
   clears, image copies). Must work headless (`Gfx::headless()`), and for demo replays (`TH08_REPLAY=demoN`) the
   frame numbers must align with the reference demo frame numbers.
2. `cargo run --release --bin drawdiff -- <reference> <port-log> [frames]`: per-frame diff (missing/extra/changed quads,
   grouped by texture label; sprite-set summary per frame), first diverging frame, and an HTML report
   (`/tmp/drawdiff/index.html`) with side-by-side renders of the port and reference for the worst frames
   (render the reference log with the port's renderer, or use the reference PNGs where they exist). Respect the
   FORMAT.md notes (fps counter ignored, title intro ±1 frame, back buffer persistence / `--playfield`).
3. Tests: replay `menu_base` and `menu_clr` key scripts (prepend the port's boot frames as README says) and compare
   against the reference logs; demo0-3 compare where chunks exist. Like `MIN_SYNC` in `src/demosync.rs`, record the
   current match level as thresholds so the tests fail only on regressions. Fix straightforward port bugs the diff
   exposes (cheap ones only); list the rest in `docs/briefs/IMPL15_QUESTIONS.md` or in your final message.

Report the per-script / per-demo first divergence and the main mismatch categories.
