# IMPL117 — spell practice files, native 19, laser restart (RE-Q50 CODE BUGs A–C) — local task

Source: `specs/changelog/answers_re_q50.md`. Implement from the numbered specs only; spec-ref comments per `CLAUDE.md`;
follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question in
`docs/briefs/IMPL117_QUESTIONS.md`.

## Deliverables

1. **Spell practice stage files** (07 §1, 04, 06 §2): with GameFlags bit 14 set, stage index 0–8 loads `stageN_s.std`
   and `ecldataNsp.ecl`; card ≥ 205 takes ECL and slot-8 enemy ANM from the card tables (205–215 stage `sp` files,
   216–221 `ecldata_xx.ecl` / `stgenm_xx.anm`). Remove the index ≥ 9 path if nothing else uses it.
2. **ECL native 19** (07 §12 row 19): int var 10000 := spell-practice card id (`game.card`, i16 sign-extended).
3. **Laser restart by entry identity** (14 §4, 09 §2, §2.1): shot init 4 treats the human and youkai sht copies as
   different entries even when they come from the same file, so a solo's focus change ends and restarts the laser.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only) and report per session
leading identical rows and first divergent row/field, before and after. Do not chase later divergences. Report the
SPEC-GAP count (was 1).
