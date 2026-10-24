# IMPL103 — SPEC-GAP batch 2, logic: bomb hold test, special-mode bomb cost, bullet warp (RE-Q36 CODE BUG 1–3) — local task

Source: `specs/changelog/answers_re_q36.md` CODE BUG list items 1–3. Implement from the cited numbered-spec sections
only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL103_QUESTIONS.md`.

## Deliverables

1. **Bomb start** (09 §1.1, §7): the bomb starts while the button is held (not newly pressed); only the special-mode
   sound uses the press test. Close the bomb.rs 450 marker (the +0xE2A7C part is right).
2. **Special-mode bomb** (09 §7, 15 §2.3): with flag bits 7–8 set the whole cost block is skipped (no bomb taken, no
   counters, no RNG draws); only the bomb index becomes 4. Close the bomb.rs 502 marker.
3. **Bullet warp, natives 4 / 7 / 21** (07 §12, 08 §2.2): the exact algorithm — per-bullet cooldown +0xDC4, zones of pos
   and pos − vel, velocity and angle reversed, scaled outward / inward, native 7's −31.1 bound quirk, hex constants as
   in the spec. Close the bullet.rs 1241 marker.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Report the
SPEC-GAP count after (was 89).
