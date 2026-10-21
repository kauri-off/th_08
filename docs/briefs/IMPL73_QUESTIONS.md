# IMPL73 questions

1. 15 §3.1 `Replay_PlayCalcDebug` 0x4526C0 (header +6 ≠ 0): frames are {input u16, flag u16, RNG state u16} and the RNG
   state is forced every frame. What does the flag word do? Are the other PlayCalc steps (key-repeat emulation, the
   fps read every 30 frames, the slow-mode / bit 9 gates, frame += 1) the same? Is the RNG forced before or after the
   input words are read, and with the stage's first 6-byte frame being the record's dummy {0, 0, RNG} (15 §3.2)?
   The port reads 3 words per frame, forces the RNG to the third, ignores the flag and otherwise runs PlayCalc.
2. 11 §1.4 `Replay_FrameHook`: is it gated on anything (GM flags bit 2, the clear bonus bit 9), or does it run every
   frame its node is linked? Does anything read +0xD8 (the debug recorder)? The port runs it unconditionally and
   only stores +0xD8.
3. 11 §4 step 10 (slow mode, cfg +0x25): which counter defines "every 3rd / 4th / 5th frame" (frame_counter, a
   private counter, 0x164D09C)? Where is gm+0x2D cleared again (top of GameMgr_Calc, the Supervisor after the OR,
   step 10 on a non-skipped frame)? Does a skipped frame return 3 before or after step 9 (score roll)? Without these
   the port does not implement step 10, so gm+0x2D stays 0 and the Supervisor's OR-accumulation (11 §7) is dormant.
4. 11 §7 OR-accumulation: on a skipped frame, is only the polled word 0x164D528 OR-ed with the raw keys (previous
   0x164D530, counter 0x164D53C and repeat flag 0x164D538 left as they are, as the port does), or is the repeat flag
   cleared?
