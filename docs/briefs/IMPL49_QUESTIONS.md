# IMPL49 questions

1. **A.65 offset check (01 §4).** The brief says "an entry offset ≥ file size"; 01 §4 says the engine checks the
   **table** offset < file size. The port checks the table offset only, per the spec. If the engine also checks entry
   offsets, 01 §4/§5 should say so.
2. **Volume step (15 §1.3, audit A.53, not in this brief).** `menu.rs` still steps volume by the repeat flag; with the
   repeat flag now set from the 33rd frame (A.55), A.53's fix should read the counter (`Input::same_frames` > 29 as
   tested before the increment, i.e. stored value > 30 after `tick`) rather than the flag.
