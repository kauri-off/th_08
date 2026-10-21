# IMPL70 — music room (audit §B) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §B (spec parts not implemented). Implement from the cited spec sections only;
remove the matching SPEC-GAP markers; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question. Use standard crates for generic needs (CLAUDE rules).

## Deliverables

1. **Music room** (16 §5.1–5.3, scene 8; `supervisor.rs`): data, title list, calc and draw as specified, replacing the stub; heard flags from score.dat.
2. **Music off** (cfg +0x1F = 0, 02 §4; `audio.rs`): no BGM; MIDI mode stays out of scope (SPEC-GAP kept).
3. Unit test of the title list / unlock logic.

When done, mark the item in audit §B with `✅ impl70` (append after the item name).
