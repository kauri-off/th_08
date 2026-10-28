# RE-Q59 — the 2 batch2 logic divergences + the menu fade quad colour

Data: re/work/runs/batch2 (REPORT.md, results.tsv, groups.tsv, drawcheck/SUMMARY.md, firstcall.tsv). Recordings:
/home/anon/Projects/th08_ext_replays/ref_b2/<name>/ and ref500/<name>/ (read-only). Port reports: re/work/runs/batch2/port/,
port traces target/batch2/<name>/, draw-log runs target/drawcheck/. Port = master (target/reb2 build). Own scratch dir
re/work/runs/q59 (CARGO_TARGET_DIR=target/re59 for a scratch port copy).

## Questions
1. gensokyou_th8_udOa25 (full, Sakuya & Remilia Lunatic 6B): rng differs at stage 2, row 30456, port rng_ctr 4 behind.
2. gensokyou_th8_udBu09 (1.00b spell practice, card 221): rng differs at stage 4A, row 8492, port rng_ctr 8 behind.
   Check whether 1 and 2 share a cause.
3. Draw: in all 20 drawcheck recordings the first draw difference is the main menu, frames 57–62, call 15: an untextured
   full-screen quad, colour fbffffff in the original vs ffffffff in the port. Find how the original computes that alpha.
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function). Use traces/draw logs
only to locate. For 1–2 rerun both plus a sample of 50 identical batch2 + ref500 recordings with the scratch fix: no regressions.

## Output
Specs + specs/changelog/answers_re_q59.md; short RE-Q59 section in re/NOTES.md; keep re/work/runs/q59/CHECKPOINT.md
current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen
only, never write to ~/Games, sessions/, specs/data/sessions/, th08_ext_replays/).
