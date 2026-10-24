# IMPL95 — stage-clear panel, continuing-stage HUD, chain-count popup (visible CODE BUGs) — local task

Source: `specs/changelog/answers_re_q32.md` §3 items 9, 12. Implement from the cited numbered-spec sections only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md` (new code written cleanly); unit-test what can be
tested without game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL95_QUESTIONS.md`.

## Deliverables

1. **Stage-clear VMs** (10 §9, 12 §5.1a): msg op 9 creates the loading VM (+0x3778) and the capture VM (+0x3CC0) with
   its 8 ghosts; the capture is taken after the next Present. Drive `Stage::hud_cover` (added in impl94) from the HUD
   cover condition (12 §5.1a, `FUN_00437d87`).
2. **Continuing stage** (12 §5.1a): the 168 stage-start tiles; `Hud_Load` on a continuing stage keeps front VMs 0–15
   and the difficulty VM (no 200-frame VM13 repaint, no fade-in).
3. **Chain-count popup** (12 §5.4): `Popup_LargeStatic` for the chain count is issued in the guarded part of
   `Hud_DrawBoss`, not every frame.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Before numbers =
current master: same 7446953 (92.16 %), changed 571287, missing 62209, extra 4232501, reordered 380593. Report the
summary after plus the capture.anm, loading00.anm, front.anm and ascii.anm group lines.
