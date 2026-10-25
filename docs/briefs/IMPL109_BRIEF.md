# IMPL109 — music room (RE-Q39 CODE BUG 1–10, IMPL108 Q1) — local task

Source: `specs/changelog/answers_re_q39.md` (all musicroom.rs rows). Implement from the cited numbered-spec sections
only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL109_QUESTIONS.md`.

## Deliverables

1. **Text** (16 §5.2, §5.3, 10 §6): colours are GDI COLORREF 0x00BBGGRR; the outline is always black (the 4th
   argument only selects the ±2 px mode); comments in 0xFFE0C0; the full 7-line warning table (U+3000 leads, line 4 a
   single U+3000); the cursor is byte 0x7F (▶, ascii sprite 126) in the row VM's colour.
2. **State / input** (16 §5.3): sub-frame reset on every state change, intro → state 1 at sub-frame 8, +2 per frame in
   state 1, Shot|Enter resets it; independent key tests in the order Up, Down, reveal, Shot|Enter, Bomb|ESC (exit
   skips Ctrl / R), Ctrl, R; two-key masks with the original edge test; on the exit frame no VM run and no draw.
3. **Draw / music** (16 §5.2, 02 §4): draw order background picture, bg VM, rows (VM, cursor, number), 7 comments,
   "Now Playing", title at (320, 52) forced white full alpha; row numbers / cursor in the row VM colour;
   `Music_PlayFile` marks flag 0 only in music modes 1/2 and not in replay/demo.

Close all 13 musicroom.rs markers. All sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos
0–3); report musicroom_practice before/after (now 3505). Report the SPEC-GAP count (was 46).
