# RE-Q50 — replay pilot: spell-practice and practice divergences

Context: specs/changelog/answers_re_q49.md (list of later divergences), re/work/runs/replay_pilot/REPORT.md, sessions in
/home/anon/Projects/th08_ext_replays/ref/ (read-only). IMPL116 is fixing RE-Q49 bugs 1–3 in parallel; ignore the
cursor, rng_ctr and loading columns.

## Questions
1. Spell practice Bu08 and JS06: first divergence at gameplay frame 2.
2. Spell practice Nd115: the port does not spawn the boss (frame 31).
3. The next earliest divergence in any other pilot session (one).
For each: what the original does → numbered spec section (add or correct) → port right or CODE BUG (src function,
read-only). Use traces only to locate; the answer comes from the code.

## Output
Specs + specs/changelog/answers_re_q50.md; short RE-Q50 section in re/NOTES.md; keep re/work/runs/q50/CHECKPOINT.md
current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git, off-screen only, never write to
~/Games, sessions/, specs/data/sessions/).
