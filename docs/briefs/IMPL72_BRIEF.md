# IMPL72 — ECL natives 4, 7, 9, 11, 13, 16, 21, 25 (audit §B) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §B (spec parts not implemented). Implement from the cited spec sections only;
remove the matching SPEC-GAP markers; unit-test what can be tested without game data. Where the spec leaves a detail
open, keep a one-line `// SPEC-GAP:` and add a question. Use standard crates for generic needs (CLAUDE rules).

## Deliverables

1. **Natives 4, 7, 9, 11** (07 §12; `eclvm.rs`): as the §12 table gives them.
2. **Natives 13, 16, 21, 25** (07 §12).
3. Unit tests per native where state can be checked without data. Natives with no data use: note the use count from the shipped ECL if the spec lists it.

When done, mark the item in audit §B with `✅ impl72` (append after the item name).
