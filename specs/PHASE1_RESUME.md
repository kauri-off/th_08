# Phase 1 (resume) — finish data formats & engine overview

Original brief: `/home/anon/Projects/th_08/specs/PHASE1_BRIEF.md` (deliverables 00..04 + extractor). A previous agent
already worked in your SPEC_DIR — its NOTES.md describes state. Continue from it; do not redo verified work.

Required at the end, in SPEC_DIR:
- `00_overview.md`, `01_archive.md`, `02_bgm.md`, `03_images.md`, `04_file_index.md` (complete, VERIFIED/INFERRED marked)
- `tools/extract_th08.py <th08.dat> <outdir>` — single pass: container → fully decoded files (all wrapper layers removed). Must extract all files.
- `tools/thtx2png.py` (or equivalent) converting any THTX/ANM texture to PNG with correct colors/alpha for every pixel format that occurs.
- In 02_bgm.md: exact intro/loop semantics so a player can loop each track seamlessly (which field is loop start, loop end, units).
- In 03_images.md: exact ANM sprite record semantics (UV rect in pixels? relation to texture size), plus a list of ANM script opcodes seen with argument sizes (semantics can be Phase 2).
- symbols.csv / structs.md / NOTES.md updated.
