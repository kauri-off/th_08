# RE-Q51 — replay pilot: "frame / ff / calc one behind" group and replay-end flags

Context: specs/changelog/answers_re_q49.md, answers_re_q50.md, re/work/runs/replay_pilot/REPORT.md; port pilot results
target/pilot/ (after IMPL116). Sessions in /home/anon/Projects/th08_ext_replays/ref/ (read-only). IMPL117 is fixing
RE-Q50 bugs A–C in parallel (src/ read-only for you; build any scratch copy with CARGO_TARGET_DIR=target/re51).

## Questions
1. About half the sessions first differ with `frame`, `ff`, `calc` one behind (udAr02 r5152, udBi01 r3670, udDn14
   r3670, udTt16 r3760, ss_51249 r6093, ss_52089 r4965, ss_52220 r5179, ss_53373 r5019, ss_82309 r5898, ss_88234 r5130).
   First rule out a fast-mode recording artifact (re-record one with `run_rpy.sh --normal` and compare). Then: what
   the original does there (replay fps stream? slowdown? stage transition?) → spec → port right or CODE BUG.
2. Spell practice replays (with RE-Q50 fixes) end ~32 rows early: `frame` one less, GameFlags bit 2 cleared one frame
   earlier at the end of the replay.
3. 52104 `score` 0x7739/0x7738 at r690 (with the RE-Q50 fixes), if time permits.
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function).

## Output
Specs + specs/changelog/answers_re_q51.md; short RE-Q51 section in re/NOTES.md; keep re/work/runs/q51/CHECKPOINT.md
current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git, off-screen only, never write to
~/Games, sessions/, specs/data/sessions/).
