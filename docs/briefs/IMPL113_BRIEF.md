# IMPL113 — menus, save dialogue, text strips (RE-Q42 CODE BUG 1–5, RE-Q43 CODE BUG 1–3, RE-Q44 CODE BUG 1–2) — local task

Sources: `specs/changelog/answers_re_q42.md`, `answers_re_q43.md` (Q2 row), `answers_re_q44.md` (Q2 row). Implement
from the cited numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit
tests. New open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL113_QUESTIONS.md`.

## Deliverables

1. **Menus** (12 §2, §2.2, 15 §1.3, §3.8): top-menu highlight only in call 0, on a cursor move and on cancel (item 7
   stays lit through the Option wait); Option press sends no range interrupt and falls through to the cancel test;
   replay-list +0x10 gate armed once per visit (file confirm / cancels 2→1, 3→2 do not reset it); key-config digits /
   ShotSlow update before the assign / toggle / Reset / exit tests and also in the exit call.
2. **Boot / restart** (00 §2): frame-skip counter starts at −4 (first boot too); restart saves score.dat before
   teardown and reloads it; game speed := 1; g_Rng reseeded from the time (call counter kept); ASCII object zeroed.
   Golden / demos must stay full — if the −4 start would shift a session, stop and report instead of fitting.
3. **Save dialogue + text strips** (16 §2.6, 10 §6): state 12 confirm does not return, cancel tested in the same
   call; state 14 cancel/ESC first; every return to the slot list (state 10 confirm, 14 cancel / "no", 13 ESC) plays
   SE 10, flushes sound, state 12, interrupt 12 to all 72 VMs, re-reads the 15 headers; `gui.rs flush_texts` and
   `menulist.rs render_strip` write the full 512-wide, 15-row strip with the caller-table x formulas (boss card name
   truncated x).

Also close the stale ending.rs markers RE-Q38 answered "right" (326, 425, 446, 467, 554) and the menu / result
markers answered by RE-Q42 / RE-Q43. All sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3); report options_cfg / musicroom_practice / gameover_save before/after (1887 / 3505 / 4214). Report the
SPEC-GAP count (was 19).
