# IMPL86 — op 128 raw words, Task_Add order, op 88 context (RE-Q31, audit D.1, D.4) — local task

Implement from the cited spec sections only; spec-ref comments per `CLAUDE.md`; unit-test what can be tested without
game data. Where the spec leaves a detail open, keep a one-line `// SPEC-GAP:` and add a question to
`docs/briefs/IMPL86_QUESTIONS.md`.

## Deliverables

1. **Op 128** (07 §5 op 128, §4 +0x53C4, 13 §2.6b; answers IMPL78 Q1): all four words a, b, c, d are copied raw (no
   variable resolution whatever the mask; d is the f32 bit pattern), and the effect spawns and centres at the base
   pos e+0x2D34, not the final pos. Replace the impl78 `SPEC-GAP` accordingly.
2. **Audit D.1** (00 §3): `Task_Add` calls on-register first, then links the node, and links it whatever on-register
   returned; no unlink on error.
3. **Audit D.4** (07 §5.4 op 88): op 88 on the caller itself calls the sub in the boss's **main** context, not the
   current (thread) context.

Mark finished items: append `✅ impl86` to audit §D items 1 and 4; add one impl86 entry to `docs/STATUS.md`.
