# RE-Q53 — replay pilot: next earliest full-game divergences

Context: specs/changelog/answers_re_q52.md, re/work/runs/q52/ (scratch port with fixes H–J), port results
target/pilot_119/. Sessions in /home/anon/Projects/th08_ext_replays/ref/ (read-only). IMPL120 is fixing H–J in src/ in
parallel (src/ read-only for you; scratch builds only with CARGO_TARGET_DIR=target/re53).

## Questions (with H–J applied in your scratch copy)
1. 51842 r2891 `score`.
2. 50715 r3680 `rng`, `score`; 80412 r4011 `rng`, `score`.
3. 51852 r4717 (Youmu solo; RE-Q49 sparkle fix is in src) and, if time permits, 53084 r7021 / Bi01 r7416.
Group sessions that share a cause. For each: original → numbered spec section (add or correct) → port right or CODE
BUG (src function). Use traces only to locate; the answer comes from the code.

## Output
Specs + specs/changelog/answers_re_q53.md; short RE-Q53 section in re/NOTES.md; keep re/work/runs/q53/CHECKPOINT.md
current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen
only, never write to ~/Games, sessions/, specs/data/sessions/, th08_ext_replays/).
