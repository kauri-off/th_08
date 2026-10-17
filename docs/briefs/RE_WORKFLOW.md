# Reverse-engineering workflow

All paths relative to the repo root. Ghidra project: `re/ghidra/th08.gpr` (pre-analyzed).

## Tools (`re/tools/`)
- `redump.sh` — apply `re/symbols.csv` to Ghidra, re-export `re/extracted/all_decomp.c` (`===== name @ addr`), `callgraph.tsv`, `globals_xref.tsv` (~50 s). Run after every batch of new symbols.
- `fn.sh <addr|name>...` — print function(s) from the dump; `fnc.sh` — same plus `_DAT_` constants annotated as f32/i32.
- `rd.py <va> [n] [h|f|i|d|s]` — read exe bytes.
- `gh.sh <Script.java> [args]` — run a Ghidra script from `re/ghidra_scripts/` (Decompile, Xrefs, Strings, ApplySymbolsOpus, DumpAll2, Disasm…). One Ghidra process at a time (project lock), ~5 s per call: batch addresses.
- Format dumpers (anm, ecl, std, msg, sht, rpy, scoredat, cfg, end, musiccmt, bgm, dat) — all must keep reporting 0 problems.
- `globals_xref.tsv` only sees direct address references; writes through a struct base pointer need a manual check.
- REA MCP (`mcp__rea__*`) is also available; its renames are session-scoped, so persist names in symbols.csv.

## Persistent memory (survives compaction)
1. `re/symbols.csv` — source of truth for names: `addr,kind,name,signature,confidence,note` (kind = func|global|label; `Class_Method`, globals `g_Name`). Append the moment you understand something.
2. `specs/structs.md` — struct layouts: offset | size | type | name | meaning | confidence.
3. `re/NOTES.md` — work log: done / in progress / next / open questions.
After every compaction or restart: re-read NOTES.md, symbols.csv, structs.md first.

## Output rules
Specs contain prose, tables, struct layouts, constants and short pseudocode describing BEHAVIOUR. Never paste decompiled code. Mark claims VERIFIED / INFERRED.
