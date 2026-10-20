# IMPL27 — comment pass, batch D (menus / files / audio / input / frame loop; tools)

Read `CLAUDE.md` (repo root) first: it defines what a comment in this port must carry.

Files: `src/menu.rs`, `src/menulist.rs`, `src/result.rs`, `src/supervisor.rs`, `src/replay.rs`, `src/scoredat.rs`, `src/config.rs`, `src/archive.rs`, `src/input.rs`, `src/audio.rs`, `src/sound.rs`, `src/task.rs`, `src/game.rs`, `src/app.rs`, `src/assets.rs`.
Tools (not ports; only a `//!` line saying what the tool does, plus comments where the code is not obvious): `src/session.rs`, `src/demosync.rs`, `src/drawlog.rs`, `src/drawreport.rs`, `src/anmdebug.rs`, `src/env.rs`, `src/lib.rs`, `src/main.rs`, `src/bin/*.rs`.
Specs to cite: 01 (archive), 02 (BGM), 11 (flow), 12 (menus), 13 (sound), 15 (files/replay/score), 16 (result), `structs.md`; others where relevant.

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
  `// SPEC-GAP:` and list it under "uncited code" in `docs/briefs/IMPL27_QUESTIONS.md`.
- **Do not restate code.** Write no comment on obvious lines.

Batches A–C (commits 090ee21, 48735eb, 3452c01) are the model for style and density. As before, when the code and the
numbered spec disagree, do not fix the code; write a SPEC-GAP and a question in IMPL27_QUESTIONS.
- Cite numbered specs only (`specs/changelog/` is evidence, not a citation).
- Keep before/after logs and file backups under `target/impl-work/` (git-ignored), not `/tmp` (they were lost between sessions last time).
