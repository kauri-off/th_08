# RE-Q57 — batch500 replays left after the AC–AL scratch fixes

Data: re/work/runs/q56/fixAL_left.tsv (first differing row per replay with the q56 scratch port = master + AC–AL;
scratch copy re/work/runs/q56/portcopy, runner prun.sh/pbatch.sh, compare scripts in re/work/runs/q56/). Recordings:
/home/anon/Projects/th08_ext_replays/ref500/<name>/ (read-only); self_sync in re/work/runs/batch500/results_master.tsv
(skip replays not "yes"). Use your own scratch dir re/work/runs/q57 (copy what you need from q56; CARGO_TARGET_DIR=target/re57).

## Questions
1. Group the leftovers by first differing field and stage (with the scratch port), then find the root cause of the
   biggest groups, earliest member first, starting with stage-1 replay silentselene_54656 r72127. After each cause,
   rerun the leftovers with the scratch fix and regroup. Aim for 3–4 root causes; stop there.
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function). Use traces only
to locate. List the replays each cause explains and the ones still left.

## Output
Specs + specs/changelog/answers_re_q57.md; short RE-Q57 section in re/NOTES.md; keep re/work/runs/q57/CHECKPOINT.md
current; end with the CODE BUG list. An implementer edits src/ in parallel (read-only for you; master moves under you,
your scratch copy does not). Rules as in RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen only,
never write to ~/Games, sessions/, specs/data/sessions/, th08_ext_replays/).
