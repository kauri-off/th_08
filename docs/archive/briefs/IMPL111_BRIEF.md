# IMPL111 — keypad input, pause / continue BGM fades (RE-Q41 CODE BUG 1, 4, 5) — local task

Source: `specs/changelog/answers_re_q41.md`. Implement from the cited numbered-spec sections only; spec-ref comments
per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question
in `docs/briefs/IMPL111_QUESTIONS.md`.

## Deliverables

1. **Key table** (15 §1.1): the full table for both input paths — keypad 8/2/4/6 and diagonals 7/9/1/3 mapped, keypad
   Enter not mapped on the default DirectInput path; a failed keyboard read returns only the joystick bits.
2. **BGM fades** (02 §4, 12 §3): `0x406AC0(2.0)` on the spell-practice pause retry — 120-frame fade-in: −10000 at once,
   then −trunc(n·5000/120) per frame, stop at −41 with no final write, normal BGM-volume scaling on every write.
3. **Continue menu BGM** (12 §4, 02 §4 modes 3/4): the BGM pause when the continue menu opens, the spell-practice
   volume dip and the 1 s fade-in on "Yes".

Also close the RE-Q41 "right" markers (audio.rs 247, sound.rs 97, eclvm.rs 414, joystick.rs 58) with spec references.
MIDI (audio.rs 237) is a separate task — leave it. All sessions stay full (golden 25634, fullrun_noclip 124707,
selftest1 1922, demos 0–3). Report the SPEC-GAP count (was 19).
