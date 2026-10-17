# RE task autocmp — reference logs from the original for automatic comparison

Goal: the port must be checked against the original automatically (no manual playtesting). The original runs in wine
with our probe DLL (re/work/hook, see TOOLING_REPORT §4). Deliverables:

1. Probe draw log. Hook the draw path (SetTexture / DrawPrimitiveUP / render states) and write, per presented frame,
   every quad: texture label (source file name, e.g. `front.anm#2` / `title00.png`, labelled at texture creation or
   ANM load), 4 vertices (x, y, z, rhw), UVs, diffuse colours, blend mode (src/dst/op + colour op), z-test/z-write,
   viewport. Define the format in `specs/data/drawlog/FORMAT.md` (text or compact binary + tool; the implementer will
   write the same format from the port, so describe it from the game's point of view, with no D3D internals needed to
   read it). Also a per-run summary: set of (texture label, UV rect) ever drawn with first frame and count.
2. Reference logs: demos 0–3 (full, frames aligned with `specs/data/demo*_trace.txt`) and a menu script (boot → title
   → each top-menu item → difficulty → character select for every team (with and without 6A/6B clears) → options →
   back), with the key script stored next to it in a form the port can replay (`TH08_INPUT` frames:mask words; add
   the menu keys you need and document them). Keep each file reasonably small (compress if needed); put them in
   `specs/data/drawlog/`. Add matching 640×480 screenshots at listed frames of the menu script.
3. Update `re/NOTES.md` and `re/TOOLING_REPORT.md` (how to regenerate the logs).
