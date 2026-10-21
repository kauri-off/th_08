# IMPL73 — replay frame hook, slow-mode input, menu flush (audit §B) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §B (spec parts not implemented). Implement from the cited spec sections only;
remove the matching SPEC-GAP markers; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question. Use standard crates for generic needs (CLAUDE rules).

## Deliverables

1. **Replay_FrameHook** prio 7 (11 §1.4, 15 §3; `replay.rs`) and the debug playback calc if specified.
2. **Slow-mode OR-accumulation of input** gm+0x2D (`supervisor.rs`; spec section from the existing SPEC-GAP).
3. **Sound flushes** after SFX 10 and on Left (`menu.rs`, `menulist.rs`) if the spec gives them.

When done, mark the item in audit §B with `✅ impl73` (append after the item name).
