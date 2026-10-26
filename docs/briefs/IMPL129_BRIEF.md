# IMPL129 — session trace: menu sampling per handler call (RE-Q55) — local task

Source: `specs/changelog/answers_re_q55.md` (CODE BUG list items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL129_QUESTIONS.md`.

## Deliverables

1. **Item 2** (specs/data/drawlog/README.md trace columns 29/30, 16 §6.1/§6.2): `menu.rs` `calc` / session tool — sample the menu screen and cursor on every MainMenu_Calc handler call (a handler returning 2 is called again in the same frame; the last call's value is the row's); screens 16/17 report the stage row / card row (`sp_row` / `lists.card`), not the shot.
2. **Result states 0x11, 0x12, 0x16** (16 §2 "Exit"): `result.rs` — they return 0 (Remove in the same calc) the same way state 2 does since IMPL127.
Expected after this task: gameover_save and musicroom_practice identical to the end (RE-Q55 scratch: 12743 / 9363).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3), plus `cargo run --release --bin session -- sessions/<name> --out target/impl129/<name> --no-drawlog` for
gameover_save and musicroom_practice (read-only input; report leading identical rows before/after). Then
`target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only) into target/pilot_129; no session may get
worse. Do not chase other divergences. Report the SPEC-GAP count.
