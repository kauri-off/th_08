# IMPL112 — MIDI music mode (RE-Q41 CODE BUG 2) — local task

Source: `specs/changelog/answers_re_q41.md` (audio.rs:237 row). Implement from 02 §5 (and 02 §4 for the shared
fade / mode logic) only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open
details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL112_QUESTIONS.md`.

## Deliverables

1. **SMF sequencer** (02 §5): parse the .mid files from th08.dat; the 1 ms timer model, tempo events, CC 2 / CC 4
   loop start / end, CC 7 scaled by the fade factor, freeze when a fade ends, init.mid played to reset the device.
   Pure logic in its own module, unit-tested on the shipped .mid files (event timing, loop jump, CC 7 scaling).
2. **Output**: a software synth crate (e.g. `rustysynth`) fed by the sequencer, using a General MIDI SoundFont found
   at run time (configurable path; common system locations such as /usr/share/soundfonts). No SoundFont found or the
   web build → log once and fall back to the WAV track (current behaviour). Do not bundle a SoundFont in the repo.
3. **Wiring** (02 §4, §5): music mode 2 (cfg +0x1F) selects the MIDI path in the same places the WAV path is chosen
   (title, stages, bosses, music room, fades); the options menu already sets the mode.

Close audio.rs 237. Logic must not change: all sessions stay full (golden 25634, fullrun_noclip 124707, selftest1
1922, demos 0–3). Never play audio on the user's machine — tests render to a buffer. Report the SPEC-GAP count (was 13).
