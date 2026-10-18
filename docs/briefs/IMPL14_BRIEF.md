# Implementer task impl14 — score.dat, replay playback, demo sync test

Read `docs/briefs/IMPL_TEMPLATE.md` first and follow it. Then docs and `specs/15_*.md`, `specs/answers_phase7.md` §3,
`specs/answers_phase8.md`, `specs/data/demo*_trace.txt`. Deliverables (ONLY these three; finish and verify one before the next):

1. score.dat (15 §2): load/save all chunks, clear masks, spell-card history (replace the session-only counters from
   impl12), practice scores, play time, unlocks. The port's save location must not be the game dir (native: next to
   the binary or a config dir; web: localStorage). `TH08_UNLOCK` keeps working.
2. Replay files (15 §3): load and play back `.rpy` (input substitution, per-stage data, speed), and the demo/attract
   mode from the title (demorpy0–3 in th08.dat) per 12 §2.2 / 11 §4. Replay recording + saving if it fits; otherwise
   leave it for the next task and say so.
3. Demo sync test: play demorpy0–3 in the port and compare every frame with `specs/data/demo*_trace.txt` (RNG state +
   counter, player position, score…). The test reports the first diverging frame and field. Fix divergences you can
   fix from the specs; list the rest as questions in `docs/briefs/IMPL14_QUESTIONS.md` with the frame and field.
Verify with `cargo test --release` (TH08_DIR), the wasm check, screenshots of the demo playing from the title.
