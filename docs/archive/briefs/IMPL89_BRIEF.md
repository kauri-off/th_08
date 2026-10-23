# IMPL89 — vars 10042–10044 / 10099, card bonus cap, live game speed in ECL clocks (RE-Q31 CODE BUG 3–6) — local task

Source: `specs/changelog/answers_re_q31.md` §3 items 3–6. Implement from the cited numbered-spec sections only;
spec-ref comments per `CLAUDE.md`; unit-test what can be tested without game data. Open details: one-line
`// SPEC-GAP:` plus a question in `docs/briefs/IMPL89_QUESTIONS.md`.

## Deliverables

1. **Variables** (07 §6): reading var 10042–10044 as a source operand (float or int) gives the final pos e+0x2D88
   (z 0); as a destination / in-place it is the pos e+0x2D34. Var 10099 = card active ? spell flag bit 2 : spell flag
   bit 9 (captured).
2. **Card bonus cap** (07 op 155, §11.1): op 155 always sets the running card's cap +0x2638 := 99 999 990;
   `Spell_Start` sets +0xFC := card bonus and cap := card bonus, or 99 999 990 if bit 27 is already set.
3. **Live game speed** (07 §5.2): the ECL clock tick and wait decrement read the current game speed, not a value
   cached at `run_thread` entry (a native 18 in the same run changes it).

Expected (RE scratch): fullrun_noclip goes from 98806 to full (124707). Raise `fullrun_noclip` in `src/session.rs`
`MIN_LEADING` to the new count.
