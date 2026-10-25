# RE-Q52 — replay pilot: GameFlags bit 10 group and next full-game divergences

Context: specs/changelog/answers_re_q51.md ("next divergences"), re/work/runs/q51/ (scratch port with fixes D–G),
sessions in /home/anon/Projects/th08_ext_replays/ref/ (read-only). IMPL118 is fixing D, E, G in src/ in parallel
(src/ read-only for you; scratch builds only with CARGO_TARGET_DIR=target/re52).

## Questions
1. Ar02 (6634), Dn14 (5048), Ro168 (6186), 53373 (47393): GameFlags bit 10 set only in the original. What sets it →
   spec → port right or CODE BUG.
2. The earliest rng / score divergence among the other full games (one or two, as time allows).
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function). Use traces only to
locate; the answer comes from the code.

## Output
Specs + specs/changelog/answers_re_q52.md; short RE-Q52 section in re/NOTES.md; keep re/work/runs/q52/CHECKPOINT.md
current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git, off-screen only, never write to
~/Games, sessions/, specs/data/sessions/, th08_ext_replays/).
