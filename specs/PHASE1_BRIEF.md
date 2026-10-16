# Clean-room brief — Phase 1: data formats & engine overview

You are the DIRTY-ROOM reverse engineer. Target: Touhou 8 (Imperishable Night) at
`/home/anon/Downloads/Touhou Collection/TH08 - Imperishable Night/TH08 - Imperishable Night/`
(th08.exe, th08.dat, thbgm.dat). Use $reverse-engineer-anything.

A separate implementer will write a Rust reimplementation from ONLY your written specs.
RULES:
- Write specifications in prose, tables, struct layouts (offset/size/type/meaning) and short pseudocode.
- Do NOT paste decompiled/disassembled code, and do not copy large literal code. Describe behaviour.
- Mark every claim as VERIFIED (tested against real files/binary) or INFERRED.
- Wherever possible, write a small verification tool (Python, under your spec dir `tools/`) proving the format, e.g. an extractor that unpacks th08.dat into `<SPEC_DIR>/extracted/` and lists files.
- Write only inside `<SPEC_DIR>`. Do not modify the game directory.

Deliverables in `<SPEC_DIR>` (markdown files):
1. `00_overview.md` — engine architecture: main loop, frame timing (60fps), render resolution (640x480), coordinate systems (playfield origin/size), list of game subsystems/managers and their per-frame update/draw order.
2. `01_archive.md` — th08.dat container format: header, encryption/obfuscation layers, file table, compression (LZSS etc) with exact parameters. Full list of contained files with sizes. Working extractor.
3. `02_bgm.md` — thbgm.dat layout and the music track table (thbgm.fmt or equivalent): per-track offset, length, intro/loop points, wave format. Which track is used where.
4. `03_images.md` — texture/image formats inside the archive (THTX or whatever exists, pixel formats), and the ANM file header + sprite table + script table layout.
5. `04_file_index.md` — what each extracted file is for (by naming pattern: stgN*.ecl, *.std, *.msg, *.anm, *.sht, etc.).

Work until all 5 files exist and the extractor works. Finish with a short summary of what is verified vs uncertain.
