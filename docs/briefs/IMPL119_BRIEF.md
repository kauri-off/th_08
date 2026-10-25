# IMPL119 — back from a watched replay: menu flow (RE-Q51 F) — local task

Source: `specs/changelog/answers_re_q51.md` row for bug F. Implement from the numbered specs only (12 §2.2 "Back from a
replay", 12 §4, 15 §2.9, 11 §4.2); spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New
open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL119_QUESTIONS.md`.

## Deliverables

1. `replay.rs` `end_playback`: after a watched replay keep GameFlags bit 3 (clear it at the switch only for demos);
   clear bits 0 and 14 as the spec says.
2. `menu.rs` `on_register` / `top`: while the menu loads, stay on screen 0 with the previous-scene cursor; switch to the
   replay screen in the top menu's entry block on the first frame after loading (12 §2.2).

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (target/pilot_118) and after. Expected: Tt16, Bu08, JS06,
Nd115 identical to the end. Do not chase other divergences. Report SPEC-GAP count (was 1).
