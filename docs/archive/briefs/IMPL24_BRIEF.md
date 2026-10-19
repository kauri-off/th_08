# IMPL24 — comment pass, batch A (ECL / enemies / bullets / items / RNG)

Read `CLAUDE.md` (repo root) first: it defines what a comment in this port must carry.

Files: `src/ecl.rs`, `src/eclvm.rs`, `src/enemy.rs`, `src/bullet.rs`, `src/item.rs`, `src/rng.rs`.
Specs to cite: 07 (ECL), 08 (bullets/items), 11 (RNG/flow), `structs.md`.

## Deliverables

1. Every file starts with a `//!` line naming what it ports and the spec sections.
2. Every non-obvious struct field, constant, opcode handler and function carries its spec section (`07 §10.1`), the
   original's name/address when the spec gives one, and units/format (fixed point, angle, frames, 0x offsets).
   Existing one-line comments that already do this stay; vague ones are rewritten.
3. Every kept quirk of the original (call order, same-frame re-run, odd clamps, original bugs, RNG call placement)
   gets a 1–3 line note saying what is kept and why, with the spec section.

## Rules

- **No behaviour change.** Do not rename, reorder or refactor code. Only comments, plus `cargo fmt`.
- **Proof of no behaviour change.** The session/demo numbers must be identical before and after:
  - golden 8055, fullrun_noclip 6265, selftest1 1422;
  - demo MIN_SYNC 4450/3869/2937/1605;
  - all tests pass.
- **Spec references must be real.** If a piece of code has no spec section behind it, do not invent one: write a one-line
  `// SPEC-GAP:` and list it under "uncited code" in `docs/briefs/IMPL24_QUESTIONS.md`.
- **Do not restate code.** Write no comment on obvious lines.
