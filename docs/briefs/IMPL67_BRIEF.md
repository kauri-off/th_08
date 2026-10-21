# IMPL67 — th08.cfg load/save, frame skip (audit §B) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §B (spec parts not implemented). Implement from the cited spec sections only;
remove the matching SPEC-GAP markers; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question. Use standard crates for generic needs (CLAUDE rules).

## Deliverables

1. **th08.cfg** (15 §1.1, §1.2): read at boot and write back after load and at exit, all fields kept (pad buttons, stick thresholds, frame skip +0x23, ShotSlow +0x26, debug flags +0x38); the thbgm.dat header probe that picks 1 or 2 (`config.rs`, `game.rs`). Native: next to score.dat; web: localStorage like score.dat. Round-trip unit test.
2. **Frame skip** cfg +0x23 (15 §1.1, 00 §2): the draw chain runs only on the frames the setting allows (`game.rs`).
3. **Supervisor +0x154** config re-check every 4000 frames (`supervisor.rs`), if the spec gives it; otherwise a question.

When done, mark the item in audit §B with `✅ impl67` (append after the item name).
