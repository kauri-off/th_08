# IMPL49 — laser cancel width, key repeat, archive checks (audit A.20, A.55, A.65) — cloud task

Source: `docs/AUDIT_SPEC_CONFORMANCE.md` §A.1. Fix the code to the spec; remove the matching SPEC-GAP markers.

## Deliverables

1. **A.20** `bullet.rs` `cancel_lasers` (08 §7): width (+0x564) := current width (+0x568), not the reverse.
2. **A.55** `input.rs` key repeat (11 §7, 15 §3.3): test the same-input counter before incrementing it, so the first
   repeat fires on the 33rd equal frame. Unit test of the first two repeat frames.
3. **A.65** `archive.rs` (01 §4, 01 §6 step 4): reject an archive with count ≤ 0 or an entry offset ≥ file size;
   an entry whose data is not compressed (no edz step) is used as is. Unit tests with synthetic archives.
