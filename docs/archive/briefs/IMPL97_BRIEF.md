# IMPL97 — darkness mask, HUD messages, "Full Power Mode!" (visible CODE BUGs) — local task

Source: `specs/changelog/answers_re_q33.md` §3 items 8, 10, 13. Implement from the cited numbered-spec sections only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md` (new code written cleanly); unit-test what can be
tested without game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL97_QUESTIONS.md`.

## Deliverables

1. **Darkness mask** (13 §4.1, 07 §12 native 0): drawn between the small and large popups — four black rects plus the
   etama.anm#4 hole sprite around the player; ECL native 0 sets its alpha / radius globals; `GameManager_StageStart`
   and `GameMgr_OnRemove` zero the alpha.
2. **HUD messages** (12 §5.5, §2.9): colours 0xFFC0B0FF (types 1, 3) / 0xFFE0B0FF (2, 4–6), scale (0.9, 1.0), advance
   read at draw time (13·0.9); types 2 "Supernatural Border!!" and 3 "CherryPoint Max!" where the spec says they are
   issued; slide position and lifetime test use the timer before its tick.
3. **"Full Power Mode!"** (08 §8.5): `Hud_ShowMessage(0, 1)` and the 2-frame panel repaint when power reaches 128 and
   on the full-power item.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Before numbers =
current master: same 7821690 (96.80 %), changed 229112, missing 29647, extra 4160688, reordered 38029. Report the
summary after plus the etama.anm#4, `-` (untextured) and ascii.anm#0 group lines.
