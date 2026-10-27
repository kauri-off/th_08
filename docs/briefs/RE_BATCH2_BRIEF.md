# RE-BATCH2 — second batch of ~500 third-party replays; draw-log check of the batch500 drawlog recordings

Tooling: re/tools/run_rpy.sh, re/tools/run_rpy_batch.sh, re/work/runs/batch500/ (selection, results and grouping scripts).
Inputs: /home/anon/Projects/th08_ext_replays/ (README.md; untrusted data, python3 -I). Our exe is 1.00d. The port
currently matches all 22 pilot and all 490 batch500 recordings (master b93b569).

## Deliverables
1. **Selection** (~500, md5-deduplicated, none of the pilot or batch500 files) in re/work/runs/batch2/selection.tsv:
   weight toward what batch500 covered thinly — Extra (~120), full games over all shot × difficulty × 6A/6B (~250),
   Tool-Assisted (~40), stage practice (~40), spell practice (~20), plus ~30 non-1.00d-index files that the exe check
   may still accept. ~20 with `--drawlog`.
2. **Run** into /home/anon/Projects/th08_ext_replays/ref_b2/<source>_<id>/ (the only place you may write under
   th08_ext_replays) with run_rpy_batch.sh, -j 12 (leave cores for the port), resumable. Results table with
   accepted / self-sync as for batch500. Port runs on master (`target/batch_run.sh`-style; own build
   CARGO_TARGET_DIR=target/reb2, output target/batch2): identical count and groups of first divergences
   (field, stage). Do not analyse causes.
3. **Draw-log check**: for the 20 batch500 recordings with a draw log, run the port session tool with the draw log
   compared (no `--no-drawlog`; output target/drawcheck/<name>) and report per recording whether the draw log
   matches, and where the first draw difference is (frame, call). Group the differences; do not analyse causes.

## Rules
Never edit src/; no git (not even git status); off-screen only (Xvfb, no audio device); never write to ~/Games,
sessions/, specs/data/sessions/; don't touch ~/.config/th08/port.cfg. Keep re/work/runs/batch2/CHECKPOINT.md current
(it must let a new agent resume); REPORT.md there; short section in re/NOTES.md. Clean up slot dirs when done.
