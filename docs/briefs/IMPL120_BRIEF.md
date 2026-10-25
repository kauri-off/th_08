# IMPL120 — spell death freeze flag, Reimu last-spell cancel quirk, D3DX SSE normalise (RE-Q52 H, I, J) — local task

Source: `specs/changelog/answers_re_q52.md`. Implement from the numbered specs only; spec-ref comments per `CLAUDE.md`;
follow `docs/PARITY_POLICY.md`; unit tests. New open details: one-line `// SPEC-GAP:` plus a question in
`docs/briefs/IMPL120_QUESTIONS.md`.

## Deliverables

1. **Spell death freeze** (09 §6.1, 11 §2.1 bit 10): `player.rs` `player_die` — the freeze is GameFlags bit 10 (so the
   sampled flags word shows it), set only in the bombs ≥ 1 branch; the death-bomb window doubling tests only that a
   card is active (no boss test).
2. **Reimu bombs** (14 §2, §2.1, §2.2): `bomb.rs` rates exactly 64.0/15.0 and 128.0/15.0; last-spell orb loop: on the
   explosion frame the orb position is still written into the orb's old cancel / damage slots (last spell only).
3. **D3DX SSE normalise** (05 §10 "Vector normalise", 06 §3 row 0x63B8, 13 §2.6a): one shared function — on x86 /
   x86_64 the native `rsqrtss` plus the correction step exactly as the spec gives (this matches the original on the
   machine it runs on); on other targets (WASM) the exact formula, with a one-line comment that it can differ in the
   last bit. Use it for `Stage_Calc`'s stored facing and the particle direction; the type 19/51/63 cull reads the
   stored facing with the dot in z, y, x order; check orbit-13 (`EffUpd_Orbit13`) and use it there if the spec says so.

Check: `zsh target/mergetools/verify.zsh .` (all sessions full: golden 25634, fullrun_noclip 124707, selftest1 1922,
demos 0–3). Then `target/pilot_run.sh` over /home/anon/Projects/th08_ext_replays/ref/* (read-only); report per session
leading identical rows and first divergent row/field, before (target/pilot_119) and after. Expected per RE-Q52: Ar02,
Ro168 full; Dn14 → 7339, 53373 → 50932, 80406 → 76752, 88234 → 62194. Do not chase other divergences. Report SPEC-GAP
count (was 1).
