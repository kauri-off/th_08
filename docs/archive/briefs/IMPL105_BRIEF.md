# IMPL105 — menus: input timing, replay screen, restart / shot type (RE-Q37 CODE BUG 2, 3, 6, 8–13) — local task

Source: `specs/changelog/answers_re_q37.md` CODE BUG list. Implement from the cited numbered-spec sections only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL105_QUESTIONS.md`.

## Deliverables

1. **Top / option menu timing** (12 §2, §2.3, 15 §1.3): top-menu cursor moves from call 9, confirm / cancel from call 19
   (port: call 10 for both); Option (top item 7) first runs at P + 30; idle exits: counter +0xC294 reset only on a non-zero
   polled input word, reset and test only from screen frame 4, exit one call later than now (items 8, 11, 12).
2. **Replay screen** (12 §2, §2.1, 15 §3.8, 00 §2): cursor / paging from call 9, confirm / cancel from call 18;
   Left / Right paging only with more than 15 files, wrapping; VM 141 reset to (640, 320) on every path into screens 11 / 16
   (a running slide is not stopped); a replay with no stage logs an error and exits (items 6, 9, 10, 13).
3. **Restart and shot type** (00 §2, 12 §2.4): return 5 restarts the whole program (tear down, boot again through logo
   and loading in the new mode); every character-screen cancel stores g_ShotType := cursor (items 2, 3).

Close the matching markers in menu.rs / menulist.rs (and the ones RE-Q37 answered "right": menu 196, 609, 921, 1057,
1386; menulist 315). All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos
0–3, and the options_cfg session if verify covers it). Report the SPEC-GAP count after (was 70).
