# RE-Q48 — implementer questions: UnPause after Music_Stop, PlaySlot heard flag (IMPL114)

Questions: `docs/briefs/IMPL114_QUESTIONS.md` (1–2); markers src/audio.rs `stop_wav` and src/menu.rs `option_run`
item 2 (read for context; do not edit src/).

## Questions
For each question: what the original does → numbered spec section → port right or CODE BUG. Q1: say what is actually
heard (stale stream data, silence, or a refilled stream) at every site that queues UnPause after Music_Stop; a run of
the original under Xvfb with audio captured to a file (no playback) is allowed if the code alone does not settle it.

## Output
Specs + specs/changelog/answers_re_q48.md (one row per question); short RE-Q48 section in re/NOTES.md; keep
re/work/runs/q48/CHECKPOINT.md current; end with the CODE BUG list.
