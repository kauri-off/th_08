# RE tooling upgrade (dirty room, SPEC_DIR=specs/opus)

Problem: `extracted/all_decomp.c` is a one-off dump (11:27) — ~1500 of 2254 functions still show `FUN_xxx` although `symbols.csv` names many of them. Agents re-derive known facts after every compaction. Xrefs need a 5 s Ghidra run, so they are rarely used.

Deliverables (max 3):

1. **Always-fresh dump.** One command `tools/redump.sh` that: runs ApplySymbols on `symbols.csv`, re-exports all functions with current names/signatures into `extracted/all_decomp.c` (same `===== name @ addr` header format so `fn.sh`/`fnc.sh` keep working), and writes `extracted/callgraph.tsv` (`addr name callers callees`) plus `extracted/globals_xref.tsv` (global → functions reading/writing it). Run it and report the new count of unnamed functions.
2. **rea pilot.** The `rea` MCP server (Ghidra provider) is available in your tool list (`mcp__rea__*`). Open th08.exe, bulk-apply names from `symbols.csv` (`set_addresses_names`), then re-check ONE already-answered question (e.g. the type-3 hit-spark condition from `answers_impl9.md`) using only rea: `procedure_pseudo_code`/`batch_decompile`, `xrefs`, `get_call_graph`. Measure: session start time, whether names stick, speed and quality vs gh.sh/all_decomp. Write findings to `specs/opus/TOOLING_REPORT.md`.
3. **Workflow update.** Based on 1–2, propose concrete edits to `specs/RE_WORKFLOW.md` (write them as a diff-style section at the end of TOOLING_REPORT.md; the coordinator applies them).

Not in scope now: running the original game (wine is not installed). Note in the report what a runtime trace (wine + apitrace / gdb breakpoints) would need.

Rules: no sub-agents, no web search, no third-party knowledge, no thcrap folder, don't touch src/, no git.
