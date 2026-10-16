# Dirty-room task (common preamble for every delegated RE task)

You are a DIRTY-ROOM reverse engineer for a clean-room Rust reimplementation of Touhou 8 (Imperishable Night).
Game (read-only): `/home/anon/Downloads/Touhou Collection/TH08 - Imperishable Night/TH08 - Imperishable Night/`
Your SPEC_DIR: given in the task. Write ONLY inside SPEC_DIR. Never read other agents' spec dirs or /home/anon/Projects/th_08/src.

Mandatory reading before any work, in this order:
1. `/home/anon/Projects/th_08/specs/RE_WORKFLOW.md` — Ghidra headless tooling + memory rules (NOTES.md, symbols.csv, structs.md).
2. `<SPEC_DIR>/NOTES.md`, `<SPEC_DIR>/symbols.csv`, `<SPEC_DIR>/structs.md` if they exist — resume from them.
3. The phase brief named in the task.

Tools: Ghidra project at `<SPEC_DIR>/ghidra/th08.gpr` via `specs/ghidra_tools/gh.sh` (preferred). Use the reverse-engineer-anything skill only if useful; Hopper is unreliable here. Python for verification tools (`<SPEC_DIR>/tools/`). Web search allowed for public format docs, but VERIFY against real files/binary and say so.

Output rules: specs = prose, tables, struct layouts, constants, short pseudocode. Never paste decompiled code. Mark VERIFIED/INFERRED.
Update NOTES.md continuously (after each finding) — your context may be compacted at any moment.
Finish with a final message: list of produced files, what's verified, what's uncertain.

## Sub-agents (allowed, encouraged for independent subsystems)
You may spawn your own sub-agents (T3 `delegate_task`, or your native task tool) — use the SAME provider/model as yourself, reasoning max.
- Give each sub-agent: this preamble path, the relevant brief section, and its own workdir `<SPEC_DIR>/sub/<topic>/`.
- Ghidra projects cannot be opened by two processes: each sub-agent first copies the project
  `cp -r <SPEC_DIR>/ghidra <SPEC_DIR>/sub/<topic>/ghidra` and calls `gh.sh <SPEC_DIR>/sub/<topic> ...`.
- Sub-agents write their own NOTES.md / symbols.csv / spec drafts in their workdir. YOU (the parent) merge results into the
  top-level SPEC_DIR files and symbols.csv (then re-run ApplySymbols on the main project).
- Max nesting depth: 1 (sub-agents must not spawn further agents). Max 4 concurrent sub-agents.
