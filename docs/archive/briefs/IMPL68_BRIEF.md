# IMPL68 — key config and joystick (audit §B) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §B (spec parts not implemented). Implement from the cited spec sections only;
remove the matching SPEC-GAP markers; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question. Use standard crates for generic needs (CLAUDE rules).

## Deliverables

1. **Key config screen** (option screen 3, 15 §1.3; `menu.rs`): the full screen as specified, stored in th08.cfg pad fields.
2. **Joystick** (15 §1.1 mapping, ShotSlow counter; `input.rs`): use the `gilrs` crate natively; on wasm the Gamepad API via web-sys (or skip with a SPEC-GAP if not feasible). Unit-test the mapping and the ShotSlow counter.
3. **Cancel on the option screen** and **return 5 / 3600-frame idle exit** (12 §2.7, 15 §1.3, `menu.rs`): implement what the spec gives; questions for the rest.

When done, mark the item in audit §B with `✅ impl68` (append after the item name).
