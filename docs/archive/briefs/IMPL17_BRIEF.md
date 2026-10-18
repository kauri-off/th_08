# impl17: answers_impl15 + main-menu lists

Deliverables:
1. Implement `specs/answers_impl15.md` and the spec fixes it lists (12 §1/§5.3/§5.9 and the menu entry rule, 13 §2.6/§3,
   16 §5.3): effect 51 particle order/colour2/double first-frame run/slot-order draw/draw-time push (diff field by field
   against `specs/data/q15/eff51_decoded.txt`), the stage-start darken overlay, gauge readout start timing, boot presents,
   loading draw mode, panel depth/z-write, stage-title sprite state, music-room capture. Check demo 1/3 draw-log match.
2. Main-menu lists from the MOPUP-1 spec work: shared ASCII text queue with the selected-row glyph set (12 §2.9),
   practice-score list (12 §2.5), replay list + detail view (12 §2.8, 16 §6.3), spell-card record screens 16/17 with the
   four pie charts and the info panel (16 §6.4–6.5). Replace the ASCII stand-ins.
3. Verify with drawdiff against `specs/data/drawlog/menu_mopup1.*` (README explains start state: its own score.dat) and
   the `menu_ref/mopup1_*.png` screenshots; add a menu_mopup1 draw-log regression test with a threshold like MENU_BASE.
   Raise MIN_SYNC / DEMO / MENU_* thresholds to the new levels and report before/after.
