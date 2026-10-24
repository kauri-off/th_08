# IMPL104 — SPEC-GAP batch 2, rest: BGM flag on reload, pause Slow label, GameMgr draw stop, 0x164D0B0 reset — local task

Source: `specs/changelog/answers_re_q36.md` CODE BUG list items 4, 5, 6, 8 and the markers it answered "right".
Implement from the cited numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow
`docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question in
`docs/briefs/IMPL104_QUESTIONS.md`.

## Deliverables

1. **Stage start / draw flow** (11 §2, §3, §4 step 3, 12 §3): gm+0x3DE28 is set at every stage start, reloads included
   (2 for a spell-practice reload whose card flag is 0, else 1; 1 plays BGM slot 0); `GameMgr_Draw` stops the draw chain
   while loading ≠ 0, scene ≠ 2, or flag bits 5–6 == 1. Close gamemgr 864 / 1072.
2. **Pause menu + 0x164D0B0** (12 §3, 11 §2, 09 §6.2): pause state 0 starts all 10 scripts, then hides script 20 unless
   practice and script 21 unless slow mode is on (close ascii 839); 0x164D0B0 reset at the real death in
   `Player_DyingUpdate`, by `Item_CollectPowerSmall` (power < 128) and at a fresh start (close player 714).
3. **Close the markers RE-Q36 answered "right"** (pshot 607, 663; bomb 787; game 102, 152; stage 371, 815; effect 467;
   anmvm 912; item 267; hud 755, 831, 1133; ascii 1023): replace each `SPEC-GAP` with a short spec-ref comment, code
   changes only where the answer says so. Leave text.rs 2 / 196 (separate task).

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Report the
SPEC-GAP count after (was 87) and the golden draw summary line.
