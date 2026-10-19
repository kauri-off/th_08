# RE-Q22: scripted reference sessions for the next port features

The port still lacks: game over → continue prompt → result screen / name entry → replay save dialogue, music room,
spell practice, option/key-config changes saved to th08.cfg. Make reference sessions the implementer can sync against
(`session` bin reads the same format as specs/data/sessions/*).

Deliverables (scripted with `re/tools/xkeys.py` on Xvfb + `record_session.sh`, work game copy only, never the user's
game folder; restore work cfg/score.dat afterwards unless the session needs a specific one — then ship it with the session):
1. `specs/data/sessions/gameover_save`: Normal, die until game over in stage 1, decline continue, result screen, enter a
   name, save the replay to a slot, back to the title. Also replay that saved replay from the replay menu if practical
   (else a second short session that does it).
2. `specs/data/sessions/musicroom_practice`: music room (move cursor, play 2 tracks, read comments), then spell practice
   (pick a stage 1 card, start it, capture or fail, return to the menu).
3. `specs/data/sessions/options_cfg`: change several options and one key binding, leave the option menu, quit the game;
   ship the resulting th08.cfg diff. Note in specs/data/sessions/README.md which spec sections each session exercises,
   plus the frame ranges of each scene, and add any spec fixes found while checking the traces.

Check each session replays bit-exact in the original (`play_session.sh`, 0 trace diffs). Keep draw logs if size is
reasonable (< 30 MB per session). Final reply: per-session summary (frames, scenes, files) and changed files.
