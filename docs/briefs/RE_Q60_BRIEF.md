# RE-Q60 — draw-log differences, part 1 (title quad, depth clear, extra ascii quads)

Logic is bit-exact on all recordings; draw must be visually identical (docs/PARITY_POLICY.md). Data:
re/work/runs/batch2/drawcheck (SUMMARY.md, firstcall.tsv, scripts/firstcall.py), re/work/runs/q59 (dc_*.txt: draw-log
compare with the RE-Q59 AU scratch fix). Draw-log recordings: /home/anon/Projects/th08_ext_replays/ref500/<name>/
(20 names in re/work/runs/batch2/drawlog.txt; read-only). Port = master; IMPL137 (RE-Q59 AT/AV/AU) is being implemented
in src/ in parallel — use re/work/runs/q59/portcopy (AT+AU+AV scratch) as the base for your scratch copy. Own dir
re/work/runs/q60 (CARGO_TARGET_DIR=target/re60).

## Questions
1. Main menu present 120–127 (udg342, udKe02): an extra `title01.anm#2` quad in the port. Next menu difference after it.
2. Gameplay frame 1–3, call 0 or 3: depth-clear colour 00000000 / ff404060 in the original vs ff000000 in the port
   (5 recordings). Which colour the original clears with, per stage/mode.
3. Gameplay calls 42–47: the port draws 2 extra ascii quads at 383.5,447.5 (4 recordings). What they are and why the
   original does not draw them.
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function). After each scratch
fix, rerun the draw-log compare on the 20 recordings: report the first difference before/after, and check the trace stays
identical.

## Output
Specs + specs/changelog/answers_re_q60.md; short RE-Q60 section in re/NOTES.md; keep re/work/runs/q60/CHECKPOINT.md
current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen
only, never write to ~/Games, sessions/, specs/data/sessions/, th08_ext_replays/).
