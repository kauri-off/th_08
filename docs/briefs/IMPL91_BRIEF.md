# IMPL91 — ECL op 88 ip, held-enemy / freed-enemy effects, Effect_Spawn budget (logic CODE BUGs) — local task

Source: `specs/changelog/answers_re_q32.md` §3 items 14–15, `answers_re_q33.md` §3 items 4–5. Implement from the cited
numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be
tested without game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL91_QUESTIONS.md`.

## Deliverables

1. **Op 88** (07 §5.4): before the push, the target context's ip := its stored ip + the size of that instruction,
   so the target's next instruction is skipped on return.
2. **Enemy effect lifecycle** (07 §10.1 step 2, §10.3b): a held enemy still runs the op-128 effect update (and the
   rest of the shared tail); `Enemy_Free` sends the aura interrupt 3 instead of freeing the aura.
3. **Effect_Spawn budget** (13 §2.2): `Effect_Spawn` / `Effect_SpawnWithParam` share one 512-slot search budget per
   call; count ≤ 0 fills slots until the budget ends; the dummy effect is returned when it is exhausted.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Report the golden
draw summary line (`ref quads … same … %`) before and after (session bin `--out`).
