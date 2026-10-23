# RE-Q33 — draw parity remainder (after RE-Q32)

Continue RE-Q32 on the golden draw log. Start from re/work/runs/q32/CHECKPOINT.md ("Remaining" section) and
specs/changelog/answers_re_q32.md; reuse the q32 scratch port (copy re/work/runs/q32/portfix to re/work/runs/q33/portfix,
fixes A–U already applied; diff in q32_fixes.diff) and rungolden.sh.

## Questions (largest first; stop chasing a group when returns get small)
1. etama.anm#1 billboard particle positions off by ≤ 0.07 px (107.6 k changed) — projection/rounding order.
2. ascii.anm#0 leftover: unexplained glyph rows (e.g. present 19480 y 338.5 x 392.5 ref vs 399.5 port), colour 7.7 k;
   separate the probe 4096-vertex truncation from real divergences.
3. etama.anm#4 never drawn by the port (2329); text.anm#0 ~1 extra quad per dialogue frame; front.anm#0 missing full
   repaints (presents 16101, 23620, 25255; 0x17CE8CC writer timing); untextured `-` missing 4.4 k; enemy/stg1enm/stg2enm
   colour/pos groups.

## Output
Every fact in the numbered specs + specs/changelog/answers_re_q33.md; short RE-Q33 section in re/NOTES.md;
keep re/work/runs/q33/CHECKPOINT.md current (rate limits happen); end with the CODE BUG list (spec § per item).
