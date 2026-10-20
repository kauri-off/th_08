# IMPL48 — music volume and fades (audit A.50, A.51, A.52) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1. Fix the code to the spec; remove the matching SPEC-GAP markers.

## Deliverables

1. **A.50** BGM volume curve (13 §1.3, 02 §4): BGM gain = 1 − (1 − v/100)²; the cube stays for SE only
   (`audio.rs` / `config.rs`). Unit test of both curves at 0, 50, 100.
2. **A.51** `audio.rs` `fade_bgm` (02 §4 `Music_Fade`): linear in dB from 0 to −50 dB over trunc(secs)·60 frames,
   then stop. Unit test of the gain at the start, middle and end frame.
3. **A.52** `menu.rs` Quit (12 §2.2): no fade of WAV music (the fade exists only for MIDI, which the port lacks).
