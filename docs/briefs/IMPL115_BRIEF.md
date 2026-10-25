# IMPL115 — WAV streaming ring: UnPause after Music_Stop (RE-Q48 CODE BUG 1) — local task

Source: `specs/changelog/answers_re_q48.md`. Implement from 02 §3 "Streaming ring" and 02 §4 "UnPause after
`Music_Stop`" only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details:
one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL115_QUESTIONS.md`.

## Deliverables

1. **Streaming ring model** (02 §3): the 4 s / 16-chunk ring, refill offset P and file position as the spec gives them,
   enough to reproduce what command 7 plays after command 3.
2. **Command 3 / 7** (02 §4): command 3 stops the buffer at position 0 and keeps the stream object; a later UnPause
   plays the ring from position 0 and refilling resumes — song continues from t + ((16−P) mod 16)·0.25 s at the last
   volume, the P = 1 "Stream Skip" case included — until the next play command.
3. Close the `audio.rs` `stop_wav` marker and the `menu.rs` item-2 marker (RE-Q48 Q2: port right).

Unit tests render to buffers (stop at a known song time, UnPause, check the resumed sample offset). Logic must not
change: all sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Never play audio on
the user's machine. Report the SPEC-GAP count (was 3; text.rs:2 stays).
