# RE-Q49 — replay pilot: two port divergences on third-party .rpy

Context: re/work/runs/replay_pilot/REPORT.md (pilot table), sessions in /home/anon/Projects/th08_ext_replays/ref/
(read-only). The port's `cargo run --release --bin session -- <dir> --no-drawlog` diverges early on every replay:

1. Replay screen (stage practice, spell practice, Extra, TAS): the original moves the stage cursor to the first
   recorded stage when a replay file is chosen; the port leaves it at 0 (trace row 97, field `cursor`).
2. Full games: first diff at the first frame of stage 1 (`rng_ctr` −4, 52089 also `rng`); the port has left stage-1
   loading one or more frames earlier than the original.

## Questions
For each: what the original does → the numbered spec section that states it (add or correct it if missing) →
port right or CODE BUG (name the src function, read-only). Use the trace/session tools only to locate; the answer
must come from the code. If (2) is fast-mode-only, prove it with a `--normal` run of the same replay.

## Output
Specs + specs/changelog/answers_re_q49.md (one row per question); short RE-Q49 section in re/NOTES.md; keep
re/work/runs/q49/CHECKPOINT.md current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git,
off-screen only, never write to ~/Games, sessions/, specs/data/sessions/).
