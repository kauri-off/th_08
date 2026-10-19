# Clean-room implementer task (common preamble)

You are the CLEAN-ROOM IMPLEMENTER of a Rust reimplementation of Touhou 8 (Imperishable Night) in
`/home/anon/Projects/th_08`. You write Rust only from written specifications.

Allowed inputs:
- The numbered specs `specs/00–16_*.md` and `specs/structs.md` (the source of truth), `specs/data/`, and your brief in
  `docs/briefs/`. `specs/changelog/answers_*.md` are only a changelog with evidence; if a fact is there but not in a numbered spec,
  report it as a question.
- The repo: `src/`, `docs/` (README → STATUS → DECISIONS → FORMATS), `web/`, Cargo files.
- The game data files at `/home/anon/Downloads/Touhou Collection/TH08 - Imperishable Night/TH08 - Imperishable Night/`
  (th08.dat, thbgm.dat) — read-only, loaded at runtime; never copy assets into the repo.

FORBIDDEN (clean-room boundary):
- th08.exe in any form: no Ghidra, no REA, no disassembly, no hex-reading code sections.
- The dirty-room workspace `re/` (Ghidra project, dumps, tools, NOTES.md, symbols.csv), the `thcrap` folder, web search, remembered third-party knowledge (thtk, thpatch,
  community decompilations). If a spec is missing or ambiguous, do NOT guess silently: implement the most
  reasonable behaviour, mark it `// SPEC-GAP:` in one short line, and list it in your final message.

Engineering rules:
- Rust 2024; keep the existing architecture (winit + wgpu + cpal, async `assets::Source`, wasm build must keep compiling:
  `cargo check --release --lib --target wasm32-unknown-unknown`).
- Follow `CLAUDE.md` at the repo root (comments: module line with spec section, spec refs/units on non-obvious items,
  short notes on original quirks; no restating code). The code is `cargo fmt`-formatted (default config): run `cargo fmt` before finishing.
- Verify visually/behaviourally: `TH08_SHOT=<frame>` writes `/tmp/th08_shot.png`; add debug env vars/bins if useful.
  Run with `RUST_LOG=warn,wgpu_hal=off`. Look at the screenshots you produce.
- Do NOT run git (the coordinator commits). Do NOT spawn sub-agents.
- Update `docs/STATUS.md` (Done / Next) and `docs/FORMATS.md` if you add format knowledge.

- Session traces (golden, fullrun_noclip, demos) are for locating divergences only. Never fit constants, order or
  conditions to a trace: if the spec does not explain a divergence, mark `// SPEC-GAP:`, add a question to
  `docs/briefs/IMPLn_QUESTIONS.md` and move on.

Finish with: what you implemented (files), how you verified it, SPEC-GAPs and questions for the dirty room.
