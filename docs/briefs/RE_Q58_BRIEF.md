# RE-Q58 — last 9 batch500 leftovers after the AC–AP scratch fixes

Data: re/work/runs/q57/fixAll.tsv (scratch port = q57/portcopy: master dfc6e03 + AC–AP). Recordings:
/home/anon/Projects/th08_ext_replays/ref500/<name>/ (read-only). Own scratch dir re/work/runs/q58 (copy portcopy and
tools from q57; CARGO_TARGET_DIR=target/re58).

## Questions
1. silentselene/gensokyou_th8_udKa49 r120959 (6B score): confirm the uncapped `AddScore` (11 §5) with a scratch fix.
2. The 8 others (stage 3: 51477 score +1; 4A: 54656 bullets −1, udPn85 bullets +1, 51759 rank +1; 4B: udCs13 rng,
   52339 bullets +1, 54010 score +1, 79317 bullets −1): find root causes, earliest first; check whether the ±1
   score/rank/bullets ones share a cause. Stop after 3–4 causes.
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function). Use traces only
to locate. After each cause rerun the leftovers plus the q57 ok set (ok_set.txt, okAll.tsv) with the scratch fix: no regressions.

## Output
Specs + specs/changelog/answers_re_q58.md; short RE-Q58 section in re/NOTES.md; keep re/work/runs/q58/CHECKPOINT.md
current; end with the CODE BUG list. An implementer edits src/ in parallel (read-only for you). Rules as in
RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen only, never write to ~/Games, sessions/,
specs/data/sessions/, th08_ext_replays/).
