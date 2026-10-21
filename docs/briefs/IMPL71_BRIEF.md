# IMPL71 — score.txt, hidden unlock code, unlock notices (audit §B) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §B (spec parts not implemented). Implement from the cited spec sections only;
remove the matching SPEC-GAP markers; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question. Use standard crates for generic needs (CLAUDE rules).

## Deliverables

1. **D key → score.txt** (16 §2.7; `result.rs`): exact text format; native writes next to score.dat, web: download or localStorage (pick one, note it).
2. **Hidden unlock code** (15 §2.12; `result.rs`).
3. **Unlock notices info00–02.jpg** (16 §4; `menu.rs`, MainMenu_OnRegister). Unit tests for the score.txt format and the code sequence.

When done, mark the item in audit §B with `✅ impl71` (append after the item name).
