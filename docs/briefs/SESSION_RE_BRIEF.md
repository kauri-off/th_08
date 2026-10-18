# Session recorder (dirty room): record a human play session in the original

Goal: the user launches the original th08 through one script, plays normally (menus included), quits; everything needed to
replay the session bit-exactly in the port and compare is saved. Build on the existing wine probe (`re/probe/`, TOOLING_REPORT §6).

Deliverables:
1. `re/tools/record_session.sh [name]`: starts th08.exe under wine with the probe in record mode, with the normal window and
   real keyboard/gamepad input, at normal speed. Recorded per game frame, from boot to exit, into `sessions/<name>/`
   (repo root, git-ignored):
   - the input mask the game actually consumed that frame (as read by the game's input function), in the port's
     `TH08_INPUT` format, plus the frame of the first title frame for boot alignment;
   - the starting state: copies of score.dat and th08.cfg as they were at launch, and every RNG seed/reseed with its frame;
   - the per-frame state trace in the same format as `specs/data/demo*_trace.txt` (columns extended if needed so menus and
     scene changes are visible: scene id, menu state), and the draw log in `specs/data/drawlog/FORMAT.md`, compressed and chunked;
   - any .rpy saved during the session.
   Keep overhead low enough that the game still runs at 60 fps; if the full draw log is too slow, make it optional.
2. Prove it: record a short session yourself with scripted keys (title → stage 1 → a few hundred frames → quit), and check that
   replaying the recorded input in the original (probe playback mode) gives identical traces/draw logs.
3. Document in `sessions/README.md` (user-facing: how to record, where files go, limits such as the pause key or alt-tab)
   and in `specs/data/drawlog/README.md` (session file formats for the port side); update re/NOTES.md and TOOLING_REPORT.
No git, no src/.
