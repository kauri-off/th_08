# IMPL130 questions

1. `src/bullet.rs` `cancel_drop` (08 §7 / §8.3): the cancels pass the raw player+0xE2A90 to `ItemMgr_Spawn`. An
   area item of −1 ("none", 09 §8 area +0x28) therefore reaches `ItemMgr_Spawn` with type −1. 08 §8.3 does not say
   what the spawn does with a negative type (the u8 store gives 0xFF, script 0x3D + 0xFF). The port's spawn returns
   no item for type < 0 (pre-existing guard). What does the original do?
