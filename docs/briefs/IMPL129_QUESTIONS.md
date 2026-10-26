# IMPL129 questions

1. **Result_Calc return 0 for states 0x11, 0x12, 0x16** (`src/result.rs` `exits`, 16 §2.4 "Exit"). The spec says these
   states "also return 0 the same way" as state 2. Open: (a) is the return gated by the same frame > 19 test, or
   unconditional in that case? (b) Is it tested on the state before or after the state handler runs? The 0x11 / 0x16
   handlers set state 10 on their first call (16 §2.1), so with a post-handler test the return is unreachable.
   (c) What enters state 0x12, and does it have a handler? The port implements: post-handler state ∈ {2, 0x11, 0x12,
   0x16} and frame > 19.
