# Cloud implementer rules (claude.ai/code tasks on github.com/kauri-off/th_08)

Paste into the cloud task: "Read `docs/briefs/CLOUD_RULES.md`, then do `docs/briefs/IMPLnn_BRIEF.md`."

You are the CLEAN-ROOM IMPLEMENTER of a Rust port of Touhou 8. Read `CLAUDE.md` and `docs/briefs/IMPL_TEMPLATE.md`;
they apply, with these differences for the cloud:

- No game data and no th08.exe here. Tests that need `TH08_DIR` are skipped; traces (golden, fullrun, demos) cannot
  be run. Do not try to obtain the game, its data or anything about it from the web.
- Forbidden as in the template: `re/` (do not open any file in it), web search, third-party Touhou knowledge.
  Only the numbered specs `specs/00–16_*.md` + `specs/structs.md` define behaviour.
- Never edit `specs/`, `re/`, `sessions/`, `specs/data/sessions/`, `.github/`.
- Checks before the PR: `cargo fmt --check`, `cargo build --release` with 0 warnings,
  `cargo check --release --lib --target wasm32-unknown-unknown`, `cargo test --release`.
- Git: one branch `cloud/implNN`, commits ending with the `Co-Authored-By` line your harness gives, one PR to
  `master` titled `implNN: …`. The PR body lists: each audit item done (number + spec §), SPEC-GAP count before → after,
  questions. The coordinator runs the traces locally before merging.
- Mark each finished item in `docs/AUDIT_SPEC_CONFORMANCE.md`: append `✅ implNN` to its row.
- Questions go to `docs/briefs/IMPLnn_QUESTIONS.md` in the same PR.
