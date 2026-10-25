# IMPL118 — calc-chain restart in sessions, continue-menu early exits, Alice laser end frame (RE-Q51 D, E, G) — local task

Source: `specs/changelog/answers_re_q51.md`. Implement from the numbered specs only; spec-ref comments per `CLAUDE.md`;
follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question in
`docs/briefs/IMPL118_QUESTIONS.md`. Bug F (back-from-replay menu flow) is a later task; don't do it here.

## Deliverables

1. **Session runner per calc pass** (00 §3, 15 §3.3, specs/data/drawlog/README.md "Sessions"): when the calc chain
   restarts inside one frame (replay fast-forward), the session tool takes raw input per `Supervisor_Calc` call from
   `polls.txt`, advances the poll index on every pass (loader sync points included) and writes one trace row per pass
   (`ff` = 1…n, then n; `calc` only on the final row). Files: `session.rs`, the restart branch in `task.rs`,
   `supervisor.rs` calc.
2. **Continue menu early exits** (11 §4.2, 15 §2.9): `ascii.rs` `ContinueMenu::update` — stage practice, replay and
   no-continue-ending exits set `game_over = 0` and displayed score := score, and add no play time.
3. **Alice laser end frame** (14 §4): `pshot.rs` `laser_update` does not return after the end branch; the option-0
   follow and trail damage rects still run that frame.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (target/pilot_117) and after. Expected per RE-Q51: Tt16, F128
full; Bu08/JS06/Nd115 full except the menu-return rows (bug F). Do not chase other divergences. Report SPEC-GAP count (was 1).
