# IMPL128 — continue menu confirm timing, menu register +0x6C, spell char cancel (RE-Q55) — local task

Source: `specs/changelog/answers_re_q55.md` (CODE BUG list items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL128_QUESTIONS.md`.

## Deliverables

1. **Items 4 + 5** (12 §4 "Confirm timing", 11 §4.2): `ascii.rs` `ContinueMenu::update` — "Yes" in spell practice / Extra acts on the press frame and clears game_over on both music branches; "No" clears game_over and sets displayed score := score 20 frames after the press; one more gameplay frame runs before the scene change.
2. **Item 7** (12 §2.2): `menu.rs` `on_register` / `top` — +0x6C set from GameFlags bit 0 for any previous scene; the switch to screen 8/15 in Top's entry block, setting bit 14 again for 15.
3. **Item 8** (16 §6.1): `menulist.rs` `spell_char_run` cancel — clear bit 0 when the menu switches back to the top screen (20 frames later), not on the Bomb press.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3), plus `cargo run --release --bin session -- sessions/<name> --out target/impl128/<name> --no-drawlog` for
gameover_save and musicroom_practice (read-only input; report leading identical rows before/after). Then
`target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only) into target/pilot_128; no session may get
worse. Do not chase other divergences. Report the SPEC-GAP count.
