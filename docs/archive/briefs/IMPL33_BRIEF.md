# IMPL33 — replace hand-rolled generic code with crates (port infrastructure)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Port infrastructure, no spec section. Game behaviour must not
change at all. Game file formats (dat archive, ANM, ECL, MSG, STD, replay, score.dat, th08.cfg, RNG) stay hand-written —
they are the port. Only generic, standard formats/platform code move to crates.

## Deliverables

1. **xz via a crate, not the external `xz` process.** Replace every `std::process::Command::new("xz")`
   (`src/drawlog.rs`, `src/session.rs`, `src/bin/session.rs`, `src/bin/drawrun.rs`) with `liblzma` (or `xz2` if
   liblzma does not build; prefer a statically built backend so no system liblzma is needed), native only. Reading
   must handle the existing `.xz` files in `specs/data/` (including concatenated streams if any exist); writing must
   produce `.xz` files the old tool reads. Keep one shared helper (open/create xz reader/writer) instead of five
   copies. Check the wasm target still builds (the code paths are native-only or cfg-gated).
2. **Platform config dir via `directories`.** Replace the hand-written `$XDG_CONFIG_HOME` / `%APPDATA%` /
   `~/Library/Application Support` logic in `src/settings.rs` (port.cfg and the save dir that shares it) with the
   `directories` crate, native only. Linux path must stay `$XDG_CONFIG_HOME/th08` (`~/.config/th08`); report the
   resulting Windows/macOS paths. Tests that set `XDG_CONFIG_HOME` must keep working.
3. **WAV parsing via `hound`.** Replace the RIFF/WAVE parser in `src/audio.rs` (`parse_wav`) with `hound` reading
   from memory (8/16-bit, mono/stereo, as today). The decoded samples for every `se_*.wav` in the archive must be
   identical to the current parser's output — add or extend a test that compares them (the existing
   `se_waves_parse` test is a start).

## Verification

- All metrics identical: golden 8104, fullrun_noclip 7552, selftest1 1422, demo MIN_SYNC 4450/3869/3081/1605,
  all draw-log metric lines unchanged, all tests pass, `cargo build --release` 0 warnings, `cargo fmt --check`,
  `cargo check --release --lib --target wasm32-unknown-unknown`.
- Run the session tool on golden with draw log and confirm the `.xz` output is readable by the port reader and by
  the system `xz -t` (as a check only; the code must not call it).
- `grep -rn 'Command::new' src` shows no `xz`.
- Update `README.md` / `docs/STATUS.md` if they mention the xz tool requirement.
- Work files under `target/impl-work/impl33/`. Never touch the real `~/.config/th08`.
