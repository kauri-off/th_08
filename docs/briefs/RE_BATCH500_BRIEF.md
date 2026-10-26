# RE-BATCH500 — reference recordings of ~500 third-party replays

Tooling: re/tools/run_rpy.sh (fast mode), re/work/runs/replay_pilot/ (selection scripts, ext_index.tsv). Inputs:
/home/anon/Projects/th08_ext_replays/ (README.md; untrusted data, python3 -I). Our exe is 1.00d.

## Deliverables
1. **Selection** (~500, deduplicated by md5, none of the 22 pilot files): stratified over the 12 shots × 5
   difficulties (Easy–Lunatic, Extra) × final A/B, plus ~40 stage practice, ~40 spell practice, ~30 Tool-Assisted,
   ~20 "debug"-tagged; prefer files whose index says 1.00d. Write selection.tsv (source, id, md5, category).
2. **Batch runner** `re/tools/run_rpy_batch.sh <selection.tsv> <out_root> -j N`: resumable (skips finished outputs),
   one log line per replay, N parallel slots (pick N for this machine: 32 cores, 30 GB). Output
   /home/anon/Projects/th08_ext_replays/ref500/<source>_<id>/ (the only place you may write under th08_ext_replays).
   No drawlog except ~20 picked across categories (`--drawlog`).
3. **Run it** and write a results table: accepted/rejected, frames, wall time, and **self-sync** = whether the
   original reached the replay's end with the score stored in the file (desynced-in-original replays are kept but
   marked). Then run the port's session tool on every accepted one (`cargo run --release --bin session -- <dir>
   --out target/batch500/<name> --no-drawlog`, CARGO_TARGET_DIR=target/re500 build from current master) and add
   leading identical rows / first divergent row+field. Group sessions by first divergent field and stage. Do not
   analyse causes.

## Output
re/work/runs/batch500/REPORT.md (+ CHECKPOINT.md kept current so the run can resume), short section in re/NOTES.md.
Rules as in RE_WORKFLOW.md (no src/ edits, no git — not even git status, off-screen only, no audio device, never write
to ~/Games, sessions/, specs/data/sessions/; under th08_ext_replays only ref500/). An implementer edits src/ in
parallel; build your port binary once at the start in target/re500 and use it for the whole table.
