# IMPL28 — endings and staff roll

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. The ending scene is a text stub today (`src/supervisor.rs`,
scene 9). Replace it with the real thing.

## Deliverables

1. **Ending object and script interpreter** — 16 §1.1–§1.6: how the game reaches scene 9 and which ending file is picked
   (§1.1–§1.2), the `.end` script format (§1.3), the per-frame interpreter order (§1.4), drawing at prio 4 with the fade
   (§1.5) and removal (§1.6). Use 10 (MSG text drawing) and 05 (ANM) where the spec points there.
2. **Staff roll** — 16 §1.7, and the "All Clear" / return to title flow — 16 §3 (including what is written to
   `score.dat` / clear flags per 15 §2 where §3 says so).
3. **Verification** — a debug switch to jump straight into an ending (e.g. `TH08_ENDING=<file or team/route>`), and
   screenshots of: one good ending, one bad ending, the staff roll, the return to the title. Look at them. Keep the
   existing full scripted run (1 → 6A → ending → result → menu) working. All metrics must stay identical:
   golden 8055, fullrun_noclip 6265, selftest1 1422, demo MIN_SYNC 4450/3869/2937/1605; all tests pass.

Every behaviour must come from the cited sections. Anything the spec leaves open → one-line `// SPEC-GAP:` plus a
question in `docs/briefs/IMPL28_QUESTIONS.md`. Keep work files under `target/impl-work/impl28/`, not `/tmp`
(screenshots from `TH08_SHOT` may stay where the tool writes them, but copy the ones you report).
