# RE-Q41 — SPEC-GAP batch 7: input, audio, sound, joystick, ECL interrupt, ascii pause fade, text filter

Markers with locations: `docs/specgaps/batch7_input_audio_misc.txt` (read the surrounding port code for context; do
not edit it). eclvm.rs:414 and ascii.rs:957 are also docs/briefs/IMPL102_QUESTIONS.md and IMPL104_QUESTIONS.md.

## Questions
For each marker: what the original does → numbered spec section → port right or CODE BUG. Update the checkpoint after
every few markers. Markers the data never reaches may be answered from code alone; say so.
- input.rs:23: the full DirectInput/GetKeyboardState key → bit table.
- ascii.rs:957: `0x406AC0` exactly (mode, frame count, start volume, per-frame formula, BGM-volume scaling).
- text.rs:196: the D3DX TRIANGLE filter call (source/dest sizes, format) precisely enough to reproduce the result.

## Output
Specs + specs/changelog/answers_re_q41.md (one row per marker); short RE-Q41 section in re/NOTES.md; keep
re/work/runs/q41/CHECKPOINT.md current; end with the CODE BUG list.
