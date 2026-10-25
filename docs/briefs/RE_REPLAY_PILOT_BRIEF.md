# RE-REPLAY-PILOT — run third-party .rpy files in the original, fast, as sessions

Inputs: /home/anon/Projects/th08_ext_replays/ (README.md there: sources, index.tsv per source; untrusted data, read-only;
copy what you need). Full-unlock save: th08_ext_replays/score_full_unlock/score.dat. Our exe is 1.00d.
Tooling to extend: re/probe/ (hook.c, session.inc), re/tools/record_session.sh, play_session.sh, menu_gen.py.
Frame loop: specs/00_overview.md `Frame_Run` (timer, deadline += 1/60, Sleep(0)).

## Deliverables
1. **Fast mode in the probe** (`TH08_FAST=1`): the timer `Frame_Run` reads (QueryPerformanceCounter, and timeGetTime
   if it is the fallback) is virtual, so every `Frame_Run` call runs a frame; no other behaviour change. Proof:
   play_session.sh golden and fullrun_noclip in fast mode → trace identical to the recording; report fps
   (normal vs fast, with and without drawlog).
2. **`re/tools/run_rpy.sh <file.rpy> <out_dir>`**: own game copy + own Xvfb display per run (so several can run in
   parallel; own wine prefix copy if needed), sound off, full-unlock score.dat, the rpy as replay/th8_ud0001.rpy,
   scripted keys open Replay → that file → first recorded stage, record mode with fast mode, exit when the replay
   ends (or on "リプレイデータが異常" / timeout). Output = a normal session directory (meta.txt, polls.txt,
   trace.txt.xz, start/ with the rpy, events.txt) so the port's `cargo run --release --bin session -- <dir>
   --no-drawlog` can replay and compare it unchanged. Add a `--drawlog` switch. Record in meta.txt: source file,
   md5, accepted/rejected, frames, wall seconds.
3. **Pilot**: pick ~20 replays covering all 12 shots, all difficulties, route A and B finals, Extra, stage practice,
   spell practice, a Tool-Assisted one, and 2–3 non-1.00d ones from gensokyou (expect rejection). Run them into
   /home/anon/Projects/th08_ext_replays/ref/<source>_<id>/, 4 in parallel. Then run the port's session tool on each
   and report per replay: accepted?, frames, original fps, port result (leading identical rows / first divergent
   frame + field). Do not fix or analyse port divergences; just list them.

## Rules
Never edit src/; no git; off-screen only (Xvfb, no audio device; never the user's display); never write to the game
folder in ~/Games, sessions/ or specs/data/sessions/; don't touch ~/.config/th08/port.cfg. Long commands in the
foreground. Write the selection, timings and results to re/work/runs/replay_pilot/REPORT.md; keep
re/work/runs/replay_pilot/CHECKPOINT.md current; short section in re/NOTES.md.
