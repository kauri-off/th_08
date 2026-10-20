# IMPL31 — one settings layer and a native launcher flow (port infrastructure)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. This task is port infrastructure, not game behaviour, so it
has no spec section; the game's own settings (`th08.cfg`, option and key-config menus: 15 §1, 12 §2.7) are NOT part of
it. Game behaviour must not change at all.

Today ~39 `TH08_*` switches are read at ~70 places in 36 files, partly through `crate::env::var` (works on the web via
URL params) and partly through `std::env` directly (silently does nothing on the web). `TH08_DIR` alone is re-read in
~27 places, mostly test and tool helpers.

## Deliverables

1. **`src/settings.rs`: one typed settings struct, read once.**
   - Sources, highest first: command-line flags, then env vars (native) or URL params (web, today's lowercase names
     without the `TH08_` prefix keep working), then the port config file (deliverable 2), then defaults.
   - Every existing switch keeps its current name and meaning, so session/demo tooling, tests and the README keep
     working. One on/off rule for every boolean switch (accept `1/0`, `true/false`, `on/off`); one error message
     style for bad values (log and use the default, never panic).
   - The struct lives in `Ctx` (or is passed where `Ctx` is not available); game modules read fields, never the
     environment. After this task only `settings.rs` (and `main.rs`/`lib.rs` entry points) may touch `std::env` or URL
     params; `src/env.rs` goes away.
   - Tests and tools: one shared helper for the game directory (e.g. `settings::test_game_dir()`), replacing the
     per-module `TH08_DIR` helpers.
   - CLI: `th08 [game dir] [--stage 4a] [--player 3] ...`: every switch also accepts `--name value` / `--name` for booleans;
     `--help` lists them with one line each.
2. **Native launcher flow (no extra screen).**
   - Game dir resolution: CLI arg → `TH08_DIR` → the saved path in the port config → a native folder dialog.
   - Folder dialog: the `rfd` crate, native target only, with a backend that needs no GTK headers at build time
     (xdg-portal on Linux). Validate the folder (it must contain `th08.dat`, case-insensitive match); if invalid, show
     an error dialog (`rfd::MessageDialog`) and ask again; on cancel, exit cleanly.
   - Port config file: plain `key = value` text, no new parser dependency, at the platform config dir
     (`$XDG_CONFIG_HOME/th08/port.cfg`, `%APPDATA%\th08\port.cfg`, `~/Library/Application Support/th08/port.cfg`; compute
     it without a new crate). Stores `game_dir` and the port-only display settings below. Write it only after a
     successful folder pick or a setting change.
   - Name lookup for game files: case-insensitive on every platform (today native is case-sensitive, web is not).
3. **Port-only display settings** in the same struct and config file: window scale (1–4, default 1 → 640×480 ×scale),
   fullscreen (Alt+Enter toggles and saves), vsync on/off. The web build ignores scale/fullscreen. These must not
   affect the logic frame loop or any trace.

## Verification

- All metrics identical: golden 8104, fullrun_noclip 7552, selftest1 1422, demo MIN_SYNC 4450/3869/3081/1605,
  draw logs unchanged, 81+ tests pass, wasm check passes.
- `grep -rn "std::env\|env::var" src` shows only `settings.rs`, `main.rs`/`lib.rs` entry points (list any other
  survivor and why).
- Run the native binary with no argument and no `TH08_DIR` and a fresh config dir (`XDG_CONFIG_HOME=target/impl-work/impl31/cfg`):
  check the dialog path at least up to the point where the dialog opens or fails gracefully headless, then with a
  saved `game_dir` in that config, check it starts without a dialog.
- Do not touch the user's real `~/.config/th08` (use `XDG_CONFIG_HOME` pointing into `target/impl-work/impl31/`).
- Update `README.md` (how to run, flags, config file) and `docs/STATUS.md`. Work files under `target/impl-work/impl31/`.
