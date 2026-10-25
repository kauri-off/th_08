# RE-Q54 — replay pilot: next earliest divergences after K–N

Context: specs/changelog/answers_re_q53.md, re/work/runs/q53/ (scratch port with fixes K–N, results fixN). Sessions in
/home/anon/Projects/th08_ext_replays/ref/ (read-only). IMPL121 is fixing K–N in src/ in parallel (src/ read-only for
you; scratch builds only with CARGO_TARGET_DIR=target/re54).

## Questions
With K–N applied, take the earliest first divergences across the pilot (expected candidates: 82309, Dn14 7339, 51249,
50715 8951, 52220, 52089, 52104 — use your own fixN table) and answer as many as time allows, earliest first, grouping
sessions that share a cause. For each: original → numbered spec section (add or correct) → port right or CODE BUG (src
function). Use traces only to locate; the answer comes from the code.

## Output
Specs + specs/changelog/answers_re_q54.md; short RE-Q54 section in re/NOTES.md; keep re/work/runs/q54/CHECKPOINT.md
current; end with the CODE BUG list and the table of first divergences with all fixes. Rules as in RE_WORKFLOW.md (no
src/ edits, no git — not even git status, off-screen only, never write to ~/Games, sessions/, specs/data/sessions/,
th08_ext_replays/).
