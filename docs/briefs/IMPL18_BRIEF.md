# impl18: session replay in the port (compare with recorded play of the original)

Sessions of the original are in `specs/data/sessions/<name>/` (format: `specs/data/drawlog/README.md` "Sessions", read it fully).
Their draw logs are outside git in `sessions/<name>/draw_*.drawlog.xz` (output of the original, allowed input like `specs/data/drawlog`).
Main target: `golden` (human play, menu → stages 1–3, 25 634 frames). Quick target: `selftest1` (1 922 frames).

Deliverables:
1. `src/bin/session.rs`: `session <session dir> [--out DIR] [--no-drawlog] [--from N] [--to N]`, headless.
   - Start state exactly as the session: `start/score.dat` and `start/th08.cfg` in a private save dir (like `drawlog::menu_start_state`), boot RNG seed = low 16 bits of the `seed` line in `events.txt`, `input.txt` as raw input (frame 1 = first main-menu frame).
   - Loader timing from `events.txt` instead of the port's own: boot, menu release and stage loading (`loader gauge/lwait`, `release stage poll P`) happen on the recorded poll index, so gameplay frame 1 runs in the same frame as the original. This replaces the fixed 30/81 loading frames for sessions (keep demos/replays working).
   - Writes the port trace in the same 36-column format (`trace.txt`, one row per poll frame) and optionally a draw log.
   - Compares with the recorded `trace.txt.xz`: rows aligned at the first main-menu row; report the first differing row with the differing columns (old/new values), the number of leading identical rows overall and per scene visit, and a per-column count. Skip columns the port can't produce meaningfully (say which) and stage-loading rows (loading ≠ 0). Then drawdiff vs the recorded draw log (reuse the drawdiff code; HTML report in `--out`).
2. Regression test (like `MIN_SYNC`): `selftest1` and `golden` leading identical trace rows ≥ the level you reach; skip when `TH08_DIR` is missing, keep the test under ~60 s.
3. Use the tool: fix the earliest divergences in `golden` that the specs already explain (e.g. the main-menu loader frame, currently one frame late at menu frame 33). For each remaining blocker write a question with frame, columns and values to `docs/briefs/IMPL18_QUESTIONS.md`.
Report before/after numbers for golden, selftest1 and the existing demo/menu thresholds (must not drop).
