# Reverse-engineering workflow (mandatory from Phase 2)

Tool: Ghidra (headless), NOT Hopper. Each agent owns a pre-analyzed project at `<SPEC_DIR>/ghidra/th08.gpr`.
Helper: `/home/anon/Projects/th_08/specs/ghidra_tools/gh.sh <SPEC_DIR> <Script.java> [args]`
- `Decompile.java <addr|name>...` — pseudocode of functions
- `Xrefs.java <addr|name>...` — who references it
- `Strings.java [substring]` — strings + referencing functions
- `ApplySymbols.java <SPEC_DIR>/symbols.csv` — (re)apply all names/signatures/comments; saves the project
Run Ghidra commands SERIALLY (one process per project, otherwise lock error). Each call ~5 s; batch many addresses in one call.
You may add your own GhidraScript .java files into `<SPEC_DIR>/ghidra_scripts/` and pass `-scriptPath` yourself, or copy gh.sh.

## Persistent memory (survives context compaction)
1. `<SPEC_DIR>/symbols.csv` — source of truth for names. Header:
   `addr,kind,name,signature,confidence,note`
   kind = func | global | label. signature = C prototype for funcs (optional), e.g.
   `0x00402830,func,AsciiManager_Init,int __fastcall AsciiManager_Init(AsciiManager *this),INFERRED,loads ascii.anm/capture.anm`
   Append a row THE MOMENT you understand something, then run ApplySymbols so later decompiles show the names.
   Naming: `Class_Method` (EnemyManager_Update), globals `g_Name`, CamelCase.
2. `<SPEC_DIR>/structs.md` — struct layouts as tables: offset | size | type | name | meaning | confidence.
   (Optional: also keep `structs.h` and apply it to Ghidra via your own script.)
3. `<SPEC_DIR>/NOTES.md` — work log: done / in progress / next step / open questions.
   **After every context compaction or restart: first re-read NOTES.md, symbols.csv, structs.md.**

## Clean-room output rules (unchanged)
Spec .md files contain prose, tables, struct layouts, constants and short pseudocode describing BEHAVIOUR.
Never paste Ghidra pseudocode into spec files. Mark claims VERIFIED / INFERRED.
