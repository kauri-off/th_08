# RE-Q36 — SPEC-GAP batch 2: rest of gameplay (23 markers)

Markers with locations: `docs/specgaps/batch2_gameplay.txt` (read the surrounding port code for context; do not edit
it). item 267, hud 755 and hud 1133 were already answered in RE-Q34 (`answers_re_q34.md`): just cite the spec §.

## Questions
For each marker: what the original does → numbered spec section → port right or CODE BUG. Group the work as:
1. Player / shots / bombs / bullets / items (pshot 607, 663; player 714; bomb 450, 502, 787; bullet 1241; item 267).
2. Game manager, stage, effects, ANM (game 102, 152; gamemgr 864, 1072; stage 371, 815; effect 467; anmvm 912).
3. HUD / ascii / text (hud 755, 831, 1133; ascii 839, 1023; text 2, 196). text 2 / 196 (GDI font, D3DX filter) are
   platform limits: only say whether anything more exact is specifiable.
Markers the data never reaches may be answered from code alone; say so.

## Output
Specs + specs/changelog/answers_re_q36.md (one row per marker); short RE-Q36 section in re/NOTES.md; keep
re/work/runs/q36/CHECKPOINT.md current; end with the CODE BUG list.
