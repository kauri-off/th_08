# IMPL23: result screen after a game, name entry, score.dat saving (playable-alpha milestone)

Goal of the milestone: a human can play title → any stage/ending → result → title with records saved. Today the
result scene (scene 6) and the result viewer are text stubs.

Deliverables:
1. Scene 6 per 16 §2.1–2.3 and §2.5: after game over (continue declined) and after an ending, the end-of-game panel,
   the name entry (`Result_NameEntry`, keyboard + pad, all glyph pages, max length, backspace/end) and the ranking
   display; then back to the title (16 §3 "All Clear" path too). The replay-save dialogue (16 §2.6) may be a stub that
   skips straight to the title: say so in STATUS.
2. score.dat writing per 15 §2.2–2.9: HSCR insertion (rank order, per difficulty/shot), CLRD/CATK/PSCR/PLST updates at
   the points the spec gives, saved to the port's save dir (never the game folder), loaded on the next start; the HUD
   hiscore uses it. Check with a round trip (save → load → save is byte-identical apart from what the spec says changes).
3. Result viewer from the main menu (16 §2.4, mode 0) showing the saved records, replacing the RESULT_MENU stub.

Verify interactively with screenshots (`TH08_SHOT`) and a scripted run (TH08_INVULN / TH08_STAGE as needed): die → no
continue → name → title → result viewer shows the entry → restart the port → still there. Keep all existing tests green
and re-measure menus (the result-viewer part of menu_mopup1 should improve). Questions to
`docs/briefs/IMPL23_QUESTIONS.md`.
