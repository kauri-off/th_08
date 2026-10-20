# IMPL42 — tools/tests ignore port.cfg; ECL chain count and chain links (RE-Q28 CODE BUGs 1–2)

Read `docs/briefs/IMPL_TEMPLATE.md` and `CLAUDE.md` first. Facts from the numbered specs only; see
`specs/changelog/answers_re_q28.md` (CODE BUG list).

## Deliverables

1. **Tests and tool runs must not read the user's `port.cfg` / localStorage** (port infrastructure, no spec §).
   Today `cargo test` and `session` pick up `~/.config/th08/port.cfg` (e.g. `invuln = on` saved from the launcher)
   and 7 tests fail / metrics change. Only the `th08` game binary (launcher or `--no-launcher` play) reads port.cfg.
   Tests, `settings::test_game_dir()` users and every `src/bin/*` tool use defaults + env/CLI only. Add a test.
2. **Var 10096** (07 §6, eclvm.rs `chain_after`): root → own count; child with a parent → the parent's count if the
   parent is a root, else 0; no parent and not a root → 0. Remove the SPEC-GAP. Expected golden 8298 → ~8508,
   fullrun 7746 → ~8166.
3. **Chain links stay visible while an enemy runs** (07 §6, enemy.rs `take`/`put`): other enemies' chain walks must
   see the running enemy's links. Expected golden → ~10516 (with RE-Q28 fix 3 also needed for the full value; report
   what you get), fullrun → ~9346.

Audit (`docs/AUDIT_SPEC_CONFORMANCE.md`): deliverables 2–3 are A.0 rows 1–2.

## Verification

- Run every metric with a `port.cfg` containing `invuln = on` in `XDG_CONFIG_HOME=target/impl-work/impl42/cfg` and
  without: results must be identical. Never touch the real `~/.config/th08`.
- Report golden / fullrun_noclip / selftest1 leading rows, demo MIN_SYNC, draw logs, SPEC-GAP, before → after; raise
  thresholds, never lower. `cargo fmt --check`, 0 warnings, wasm check, all tests pass.
- Questions to `docs/briefs/IMPL42_QUESTIONS.md`. Work files under `target/impl-work/impl42/`.
