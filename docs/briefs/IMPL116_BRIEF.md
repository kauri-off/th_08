# IMPL116 — replay pilot fixes (RE-Q49 CODE BUGs 1–3) — local task

Source: `specs/changelog/answers_re_q49.md`. Implement from the numbered specs only; spec-ref comments per `CLAUDE.md`;
follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question in
`docs/briefs/IMPL116_QUESTIONS.md`.

## Deliverables

1. **Youmu solo option sparkle** (14 §3.3): `pshot.rs` `place_option` spawns no effect 0x2F when unfocused and the
   direction code is 0.
2. **Replay stage start checksum** (11 §3.1, §1.4): `gamemgr.rs` `GameManager::on_register`, replay branch, after the
   stage record load: one `Stats::checksum` with the RNG state saved and restored (the draws still count).
3. **Replay menu shared cursor** (15 §3.8): `menulist.rs` `replay_run` uses one cursor for list row, stage row and
   speed with the writes and the −1 → 9 wrap the spec gives.

Check: all sessions stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3); `zsh
target/mergetools/verify.zsh .`. Then run the session tool on every pilot session in
/home/anon/Projects/th08_ext_replays/ref/* (`cargo run --release --bin session -- <dir> --out target/pilot/<name>
--no-drawlog`; read-only input) and report per session the leading identical rows and the first divergent row/field
before and after. Do not chase later divergences. Report the SPEC-GAP count (was 1; text.rs:2 stays).
