# IMPL69 — replay save dialogue (audit §B) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §B (spec parts not implemented). Implement from the cited spec sections only;
remove the matching SPEC-GAP markers; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question. Use standard crates for generic needs (CLAUDE rules).

## Deliverables

1. **Replay-save dialogue** (16 §2.6, Result states 10–14; 15 §3.6 save flow incl. skip tests for changed config / recorded slow mode and the slowdown fields; `result.rs`, `replay.rs`). Keep `TH08_REPLAY_SAVE` working for tools.
2. **Replay file fields** (15 §3.5): clear status +0x11C, card name +0x7E, 0x164D0B0, USER section as specified (`replay.rs`).
3. Unit test: a saved replay parses back with the same header fields.

When done, mark the item in audit §B with `✅ impl69` (append after the item name).
