# IMPL34 — release builds: GitHub Action producing a Windows NSIS installer and a Linux AppImage

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Port infrastructure, no spec section, no game behaviour
change. The game data is never bundled: the package contains only the port binary; the launcher asks for the
user's Touhou 8 folder (impl31/impl32).

## Deliverables

1. **`.github/workflows/release.yml`.**
   - Triggers: push of a tag `v*` and `workflow_dispatch`. Existing `pages.yml` stays untouched.
   - Job `windows` on `windows-latest`: `cargo build --release` (x86_64-pc-windows-msvc), then an NSIS installer
     (makensis is preinstalled on the runner or install it in the job) from a script in the repo.
   - Job `linux` on an old-enough Ubuntu runner for glibc compatibility (say which and why): release build, then an
     AppImage (linuxdeploy/appimagetool or cargo-appimage — pick one, pin versions/checksums of downloaded tools).
     It must run without system packages beyond what a desktop has (Vulkan/GL loader and audio via the host is
     fine; check what `ldd` shows and bundle or exclude libs deliberately).
   - Both jobs upload artifacts; on a tag push a job creates/updates the GitHub Release and attaches both files.
     Use `Swatinem/rust-cache`. Least-privilege `permissions`.
2. **Packaging files.**
   - `packaging/windows/th08.nsi`: per-user or per-machine install (pick and justify), Start-menu shortcut, optional
     desktop shortcut, uninstaller, add/remove programs entry, version from the tag or `Cargo.toml`. License GPL-3.0
     page from `LICENSE`.
   - `packaging/linux/`: `.desktop` file, an icon (create a simple original icon, do NOT extract or use any asset
     from the game files), AppRun if needed.
   - The Windows binary must not open a console window (`windows_subsystem = "windows"` on release builds) unless
     that breaks `--help` output — say how you handled it.
3. **Local checks and docs.**
   - Check the Windows build compiles locally with `cargo check --release --target x86_64-pc-windows-gnu` (target
     installed); fix any Windows-only compile errors in `src/`.
   - Build the AppImage locally (same script as CI) under `target/impl-work/impl34/` and start it with
     `--help` and with `TH08_SHOT` headless-style if possible; report what could not be checked (NSIS runs only in CI).
   - Script the packaging steps so CI just calls them (`packaging/linux/build-appimage.sh`,
     `packaging/windows/build-installer.ps1` or a makensis call).
   - README: download/install section. `docs/STATUS.md` entry.

## Verification

- Game metrics untouched (no game code changes expected; if `src/` changes, rerun golden/fullrun/selftest/tests).
- `cargo fmt --check`, 0 warnings, wasm check.
- Do not run git and do not push; the orchestrator pushes and runs the workflow via `workflow_dispatch`.
- Work files under `target/impl-work/impl34/`.
