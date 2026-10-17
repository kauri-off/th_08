# RE phase 8 — RUNTIME-1: wine pilot on the original (dirty room)

From the ranked list in `re/NOTES.md` (phase 7). Wine via PortProton (paths in RE_WORKFLOW). Use your own WINEPREFIX and a COPY of the game dir under `re/work/` (never modify the original dir). Xvfb is available for headless runs. Use gdb/winedbg, Frida, or a small injected DLL/hook — whatever works.

Deliverables (max 3):

1. **x87 control word** after CreateDevice and during Frame_Run → close the INFERRED single-precision claims (05 §10, 11 §1.2). Fix specs in place.
2. **Ground-truth trace** while playing each demo replay (demorpy0..3): per frame RNG state + call counter, player position, score (plus anything cheap and useful for sync, e.g. bullet/enemy counts). Write it as compact text/CSV into `specs/data/` (data only, no code) and document the format in `specs/answers_phase8.md`, so the implementer can build a replay-sync regression test against it.
3. **Reference screenshots** of the original for known visual questions: natives-3 mask, an ending fade, the spell-card ring, a boss under fire. Save PNGs into `specs/data/ref/` with frame/scene noted in answers_phase8.md.

If wine cannot run the game, report exactly what fails and what would be needed. Write the runtime procedure (commands, hooks) into `re/TOOLING_REPORT.md` so it can be reused.
