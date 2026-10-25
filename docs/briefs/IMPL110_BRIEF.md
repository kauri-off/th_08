# IMPL110 — replay, score.dat, supervisor (RE-Q40 CODE BUG 1–5, RE-Q43 CODE BUG 4) — local task

Sources: `specs/changelog/answers_re_q40.md`, `answers_re_q43.md` (Q3 row). Implement from the cited numbered-spec
sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details:
one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL110_QUESTIONS.md`.

## Deliverables

1. **ExeCheck** (15 §2.10, §2.1, §3.7): parse `th08_0100d.ver` from th08.dat (15 lines `tag size sum`, wrapping
   32-bit); every VRSM v1 chunk of score.dat and the replay info block (+0x12C / +0x124 / +0x128) go through it; a
   failure rejects the whole file as the spec says.
2. **Replay file** (15 §3.2, §3.3, §3.5): USER text キャラ名 keeps its full-width padding (tables per §3.5); fps
   sample 0 is the leftover value (0 after boot, else the last one); fast-forward only while gameplay runs and the
   clear bonus is not shown, dialogue test first on the replay frame counter, fast test only otherwise.
3. **CATK at game start** (15 §2.2, §2.5, §2.12): `GameMgr_LoadScoreData` zeroes and stamps all 222 records (magic,
   version 3, id) before loading score.dat; `Spell_Start` writes name and owner, then tests the checksum against the
   new name (bytes up to the NUL); drop the `present` guard.

Also close the RE-Q40 "right" markers (scoredat 590, supervisor 36/112/270/377, config 166, replay 571/702/742) with
spec references. All sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3); report
gameover_save before/after (now 4214). Report the SPEC-GAP count (was 33).
