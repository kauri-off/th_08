# IMPL94 — Stage_DrawHigh gates, item draw, Spell_End name plate (visible CODE BUGs) — local task

Source: `specs/changelog/answers_re_q32.md` §3 items 4–5; `answers_re_q33.md` §3 item 7. Implement from the cited
numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be
tested without game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL94_QUESTIONS.md`.

## Deliverables

1. **Draw gates** (06 §10.2): `Stage_DrawHigh` draws list-B effects and the B24 = 1 fade rect (black, alpha
   B28·255/60, rect 32,16–416,464) only while +0xB24 < 2 and the HUD cover condition is off; the same HUD cover
   condition gates `Stage_DrawLow` steps 4 and 7.
2. **Item draw** (08 §8.6): `ItemMgr_Draw` sets sprite / colour / zwrite-off only when the item's on-screen byte
   (+0x2D6) flips (on spawn: 1, colour white), not every frame.
3. **Spell end** (07 §11.1, 12 §5.8): `Spell_End` zeroes 0x4E3D28, then calls `Spell_HideName` when the card was active,
   so the card-name plate and the bonus line leave the screen.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Before numbers =
current master: same 7255734 (89.79 %), changed 759669, missing 65046, extra 4667780, reordered 393333. Report the
summary after plus the etama.anm#1, item and text.anm group lines.
