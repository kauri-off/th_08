# IMPL106 — menus: Info screen loop, description VM, key-config VMs, card-name VM (RE-Q37 CODE BUG 1, 4, 5, 7) — local task

Source: `specs/changelog/answers_re_q37.md` (rows menu.rs:136, 948, 1210, menulist.rs:1354). Implement from the cited
numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open
details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL106_QUESTIONS.md`.

## Deliverables

1. **Info screen loop** (16 §4): per iteration draw t → poll → Present → test → t := 5980 → t += 1, so the jump shows
   one iteration after the press (t = 5981); the edge test, the bound and the quad size (639×479) as in 16 §4.
2. **Description VM +0xC2BC and key-config VMs** (12 §2.1, §2.2, 15 §1.3): drawn while +0xC2BC ≠ 0 with the full
   writer list (option / key-config descriptions, hidden during the Quit and Option waits, not on the difficulty /
   replay first frame); key-config screen through VMs 44 heading, 45–56 rows, 57–74 digit pairs from the working
   copy, 75/76 ShotSlow, descriptions table 0x4C8690 — replacing the ASCII rows.
3. **Card-name VM** (12 §2.8 step 3): draw it on the spell-practice / replay screen as specified.

Close the markers (menu.rs 136, 948, 1210; menulist.rs 1354) and any other remaining menu markers the cited sections
answer. All sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3); report options_cfg,
musicroom_practice, gameover_save numbers before/after (now 1887 / 3505 / 4214). Report the SPEC-GAP count (was 60).
