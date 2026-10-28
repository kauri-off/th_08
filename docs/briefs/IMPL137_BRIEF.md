# IMPL137 — effect spawn-time game speed, Vec3 dot order, screen effect initial alpha (RE-Q59) — local task

Source: `specs/changelog/answers_re_q59.md` (CODE BUG items named below). Implement from the numbered specs only;
spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL137_QUESTIONS.md`.

## Deliverables

1. **AT** (13 §2.2 "Spawn-time game speed"): `effect.rs` — an effect's script starts inside the spawn with the spawn
   frame's game speed (no deferred start at the next EffectMgr_Calc); `spawn_rng` / the type inits (EffInit_Spark etc.)
   get the current game speed, not 1.0.
2. **AV** (13 §2.6a): the type-51 cull dot product sums (x·x' + y·y') + z·z' in f32 (Vec3_Dot order); check other
   callers of the same dot helper against the spec.
3. **AU** (13 §3 "Initial alpha", "Title fade"; 12 §1): `supervisor.rs` `end_loading` registers the title fade so its
   first calc runs before its first draw (as the original), and `screen_fx` objects start with alpha 0 (zero-filled),
   not a preset 255 / A.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
gameover_save 12743, musicroom_practice 9363, options_cfg 4743, demos 0–3). Then `target/pilot_run.sh target/pilot_137`
(22 replays, all identical), `target/batch_run.sh target/batch_137` (ref500, 490 recordings) and
`E=/home/anon/Projects/th08_ext_replays/ref_b2 BASE=target/batchb2_identical_latest.txt target/batch_run.sh target/batchb2_137`
(498 recordings, incl. gensokyou_th8_udBu09 and gensokyou_th8_udOa25 which must become identical). Each ~20 min, run
them in the background without a short timeout; inputs read-only. Report identical counts and regression lists (must be
empty) and the SPEC-GAP count. No git; do not touch re/, specs/ or th08.exe.
