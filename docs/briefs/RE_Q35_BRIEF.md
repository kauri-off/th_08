# RE-Q35 — SPEC-GAP batch 1: ECL VM and enemies (17 markers)

The port has 105 `// SPEC-GAP:` markers. This batch covers the 17 in `src/eclvm.rs` and `src/enemy.rs`, listed with
their location in `docs/specgaps/batch1_ecl_enemy.txt` (read the surrounding port code for context; do not edit it).

## Questions
For each marker: what the original does → write it into the numbered spec section → say whether the port's current
assumption is right or a CODE BUG. Group the work as:
1. Interrupts and contexts (eclvm 360, 414, 1344) and random / var reads (239, 1291, 1364).
2. Natives and spell start (1130, 1217, 1239, 1250, 1415, 1439) and ops 86 / 92 (1851, 724).
3. Enemy (enemy 878, 1635, 2530).
Markers the data never reaches may be answered from code alone; say so.

## Output
Specs + specs/changelog/answers_re_q35.md (one row per marker: file:line → answer → spec § → right / CODE BUG); short
RE-Q35 section in re/NOTES.md; keep re/work/runs/q35/CHECKPOINT.md current; end with the CODE BUG list.
