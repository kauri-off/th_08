# RE-Q55 — op 109 filters; gameover_save and musicroom_practice divergences

## Questions
1. `docs/briefs/IMPL121_QUESTIONS.md` Q1: does ECL op 109 (fire stored descriptor) go through `Ecl_FireBullets`'
   filters (mode flags, which bit; no-fire radius) and the 07 §9.2 rank add, or straight to the pattern spawn?
2. sessions/gameover_save (first diff row 4215) and sessions/musicroom_practice (row 3506) differ in the current port
   (`cargo run --release --bin session -- sessions/<name> --no-drawlog`, output to target/re55/; read-only input).
   They were not part of verify.zsh; find each first cause.
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function). Use traces only
to locate.

## Output
Specs + specs/changelog/answers_re_q55.md; short RE-Q55 section in re/NOTES.md; keep re/work/runs/q55/CHECKPOINT.md
current; end with the CODE BUG list. An implementer edits src/ in parallel (read-only for you; scratch builds only with
CARGO_TARGET_DIR=target/re55). Rules as in RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen
only, never write to ~/Games, sessions/, specs/data/sessions/, th08_ext_replays/).
