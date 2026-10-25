# IMPL114 — MIDI / BGM fixes (RE-Q46 CODE BUG 1–6) — local task

Source: `specs/changelog/answers_re_q46.md`. Implement from the cited numbered-spec sections only (02 §4, §5, 15 §1.3,
12 §2.7); spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL114_QUESTIONS.md`.

## Deliverables

1. **Sequencer** (02 §5): tempo event 0x51 built as v·257 + b per byte; +0x2CC starts at 0 at boot and, with the raw
   CC 7 bytes, carries across songs; CC 4 with no earlier CC 2 and status 0xF7 / 0xF1–0xFE exactly as 02 §5 says.
2. **Mode switches** (15 §1.3, 02 §4): option Reset from MIDI sets WAV mode with no music call (the MIDI song keeps
   playing); `play_wav` / `stop_bgm` call `midi_stop` only in MIDI mode; option item 2 Left-from-MIDI plays init.mid.
3. **WAV fade / pause** (02 §4): `stop_bgm` clears the fade; a fade keeps ticking while paused, and if it ends during
   the pause the unpause resumes at the last fade volume.

Close the midi.rs / audio.rs markers RE-Q46 answered. Logic must not change: all sessions stay full (golden 25634,
fullrun_noclip 124707, selftest1 1922, demos 0–3). Never play audio on the user's machine. Report the SPEC-GAP count
(was 9).
