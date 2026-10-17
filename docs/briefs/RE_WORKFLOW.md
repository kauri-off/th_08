# Reverse-engineering workflow

All paths relative to the repo root. Ghidra project: `re/ghidra/th08.gpr` (pre-analyzed).

## Tools (`re/tools/`)
- `redump.sh` — apply `re/symbols.csv` to Ghidra, re-export `re/extracted/all_decomp.c` (`===== name @ addr`), `callgraph.tsv`, `globals_xref.tsv` (~50 s). Run after every batch of new symbols and at the start of a run if all_decomp.c is older than symbols.csv.
- `fn.sh <addr|name>...` — print function(s) from the dump (0.03 s; the default way to read code); `fnc.sh` — same plus `_DAT_` constants annotated as f32/i32.
- Callers/callees: grep `re/extracted/callgraph.tsv` (addr, name, callers, callees) before running any Ghidra script. Indirect calls (func-chain, vtables, effect/bomb tables) are not listed.
- `rd.py <va> [n] [h|f|i|d|s]` — read exe bytes.
- `gh.sh <Script.java> [args]` — run a Ghidra script from `re/ghidra_scripts/` (Decompile, Xrefs, Strings, ApplySymbolsOpus, DumpAll2, Disasm…). One Ghidra process at a time (project lock), ~5 s per call: batch addresses.
- Format dumpers (anm, ecl, std, msg, sht, rpy, scoredat, cfg, end, musiccmt, bgm, dat) — all must keep reporting 0 problems.
- `globals_xref.tsv` only sees direct address references; writes through a struct base pointer need a manual check.
- REA MCP (`mcp__rea__*`, provider ghidra): fresh import, not `re/ghidra`; first query ~40 s. No thiscall fix/signatures (`this` = `in_ECX`, helper args dropped) — check struct offsets with `fn.sh`.
  Good for `xrefs` (<0.1 s), `search_bytes` (whole image), `get_call_graph`. `set_addresses_names` works but is session-scoped and costs ~40 KB context: apply only the names you need.
- Runtime (wine via PortProton, not on PATH): `~/PortProton/data/dist/WINE_LG_11-1/bin/wine`, `~/PortProton/data/dist/PROTON_LG_10-28/bin/wine` (also flatpak `ru.linux_gaming.PortProton`), prefix `~/PortProton/data/prefixes/DEFAULT` (has winedbg.exe). Use a separate WINEPREFIX for experiments; never modify the game dir. gdb, rizin, Xvfb are installed.
- "Only call site / only writer" claims: prove them with a byte-pattern search, then check every non-constant site against the data dumps (ecl_dis, anm_dis…).

## Persistent memory (survives compaction)
1. `re/symbols.csv` — source of truth for names: `addr,kind,name,signature,confidence,note` (kind = func|global|label; `Class_Method`, globals `g_Name`). Append the moment you understand something.
2. `specs/structs.md` — struct layouts: offset | size | type | name | meaning | confidence.
3. `re/NOTES.md` — work log: done / in progress / next / open questions.
4. `re/TOOLING_REPORT.md` — tool timings/limits; read once per run.
After every compaction or restart: re-read NOTES.md, symbols.csv, structs.md first.

## Output rules
Specs contain prose, tables, struct layouts, constants and short pseudocode describing BEHAVIOUR. Never paste decompiled code. Mark claims VERIFIED / INFERRED.
