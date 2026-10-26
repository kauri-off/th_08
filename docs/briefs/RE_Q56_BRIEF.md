# RE-Q56 — top divergence groups from the 490-replay batch; result states 0x11/0x12/0x16

Data: re/work/runs/batch500/results_master.tsv and groups_master.tsv (port built from master dfc6e03, reports in
port_master/<name>.txt, port outputs in target/batch500m/<name>). Recordings:
/home/anon/Projects/th08_ext_replays/ref500/<name>/ (read-only). Reproduce one with
`cargo run --release --bin session -- <ref500 dir> --out target/re56/<name> --no-drawlog` (CARGO_TARGET_DIR=target/re56).
Skip replays whose self_sync is not "yes".

## Questions
1. **Extra, rng** (53 replays, stage Ex, first differing gm 1956–62046). Earliest: silentselene_52381 (row 2146),
   gensokyou_th8_udFc15, silentselene_53308. Find the first cause; then check whether the later members of the group
   (e.g. the median ~40k) are the same cause or another one.
2. **Stage 1, bullets** (28 replays, gm 7807–13650). Representatives: silentselene_52723, silentselene_51969,
   silentselene_53714.
3. **Stage 6A/6B, gauge** (22 + 9 replays). Representatives: silentselene_50763, silentselene_51844 (6A),
   silentselene_52245 (6B).
4. `docs/briefs/IMPL129_QUESTIONS.md` Q1 (Result_Calc exit for states 0x11/0x12/0x16: gate, test before/after the
   handler, what enters 0x12).
For each: original → numbered spec section (add or correct) → port right or CODE BUG (src function). Use traces only
to locate. If one cause explains a whole group, say so; list members that are not explained.

## Output
Specs + specs/changelog/answers_re_q56.md; short RE-Q56 section in re/NOTES.md; keep re/work/runs/q56/CHECKPOINT.md
current; end with the CODE BUG list. Rules as in RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen
only, never write to ~/Games, sessions/, specs/data/sessions/, th08_ext_replays/).
