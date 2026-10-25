# IMPL107 — result screen: hidden code, VM 71 fade, rank > 9 insert, header colour, slot validity, cancel order (RE-Q38) — local task

Source: `specs/changelog/answers_re_q38.md` (rows result.rs:329, 888, 949, 1041, 1335, 1386, 1406 and "cancel before
confirm"). Implement from the cited numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow
`docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question in
`docs/briefs/IMPL107_QUESTIONS.md`.

## Deliverables

1. **Hidden code** (15 §2.12, 16 §2.4): page input first, a confirm/cancel call returns before the code step; release
   of Focus+Skip → 0; wrong key = edge on 0x160B → 0, arrows / D never reset; effect one call after the 10th key; all
   13 story attempt counters (+0x124) of all 222 records +1, no magic test / cap / checksum refresh.
2. **Result draw** (16 §2.1, §2.2, §2.6): VM 71 interrupt 18 every state-0xF call with frame ≤ 30 (panel fades over
   30–60); rank > 9 slide-in: interrupt 2 overwrites d + 3 in the same call and LSNM is copied into +0x58; state-13
   header colour = the last grid cell's colour (leftover rule).
3. **Pages** (16 §2.4, §2.6): every result menu page tests cancel before confirm; a replay slot whose `Replay_Load`
   fails counts as empty.

Close the markers above in result.rs. All sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3); report gameover_save, options_cfg, musicroom_practice before/after (now 4214 / 1887 / 3505). Report the
SPEC-GAP count (was 57).
