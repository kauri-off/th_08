# IMPL96 — score popups, score / hiscore rows, bonus-line digit (visible CODE BUGs) — local task

Source: `specs/changelog/answers_re_q32.md` §3 items 2–3; `answers_re_q33.md` §3 item 9. Implement from the cited
numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be
tested without game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL96_QUESTIONS.md`.

## Deliverables

1. **Popups** (13 §4): small and large popups drawn through a VM with `Draw2DSnap`, centred (the init call cancels the
   anchor flag), small popups at z 0.1; colour bytes in BGRA order (the port swaps R/B of large popups); fade distance =
   player pos − popup screen pos (no origin correction); freed at age > 60 / > 90 (check the large-popup part impl95
   already changed); large-popup x0 = pos.x − 3.5·(stored glyphs incl. '+').
2. **Score rows** (11 §5, 15 §2.3, 12 §5.3 row order): the score row (y 56) is queued before the hiscore row (y 40);
   the hiscore-continues value stats+0x18 starts from the top score.dat entry (+0x26).
3. **Bonus line** (12 §5.8): the captures field advances only between digits, not after the units digit.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Before numbers =
current master: same 7475377 (92.51 %), changed 571165, missing 33907, extra 4204288, reordered 379188. Report the
summary after plus the ascii.anm#0 group line.
