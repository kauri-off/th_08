# Clean-room brief — Phase 2: script VMs & core gameplay

Same role and rules as Phase 1 (TASK_TEMPLATE.md, RE_WORKFLOW.md). Continue in your existing SPEC_DIR: re-read your
NOTES.md, symbols.csv, structs.md and your Phase 1 specs first; extend symbols.csv as you go.

Goal: the implementer must be able to run the game's own scripts (ANM, STD, ECL, MSG) and reproduce core gameplay
frame-exactly. Describe behaviour per frame: order of operations, units, integer vs float, rounding, RNG use.

Deliverables in `<SPEC_DIR>`, in this priority order (finish and verify one before moving on):
1. `05_anm_vm.md` — ANM script interpreter: per-instance state (struct layout), per-frame update order, timing
   (time field, waits, interrupts/labels), every opcode used in th08's ANM files (number, args with types, exact effect),
   interpolation modes, blend modes, how a sprite instance is drawn (position/scale/rotation/anchor/colour/UV, 2D vs 3D).
   Tool: a disassembler that prints every script of every .anm with opcode names; assert all opcodes in data are covered.
2. `06_std.md` — stage background (.std): file layout, object/quad tables, instance placement, script opcodes
   (camera, fog, etc.), how the 3D camera and fog are set per frame. Tool: parser/dumper for all .std files.
3. `07_ecl.md` — enemy script (.ecl): file layout, sub/timeline structure, VM state (variables, stack, registers,
   per-enemy fields), every opcode used in data with exact semantics, enemy struct, spawn/kill/drop rules,
   bullet-spawn opcodes and their parameters. Tool: disassembler for all .ecl files with full opcode coverage.
4. `08_bullets_items.md` — bullet manager (struct, max counts, motion modes, graze, cancel/clear), laser types,
   items (types, physics, auto-collect line, values), point/graze/time-orb scoring as far as code shows.
5. `09_player.md` — player movement speeds (focused/unfocused, diagonal), hitbox sizes, shot types (.sht format),
   bombs, deathbomb window, lives/bombs/power rules, input bitmask mapping.
6. `10_msg.md` — dialogue (.msg) format and opcodes, portrait/text display, interaction with stage flow.
7. `11_rng_and_flow.md` — RNG algorithm and seeding, stage flow (stage start/end, boss/spell-card sequence, timers,
   spell-card bonus), scene state machine (title/menu/game/pause) as far as needed to drive stages.

Each spec: struct layouts as tables, opcode tables (number | name you assign | args | effect | VERIFIED/INFERRED),
short pseudocode for algorithms. Never paste decompiled code. Verification tools go in `tools/`.
If you run low on time, a complete and verified 05–07 beats shallow coverage of all seven files.
Finish with: produced files, what is VERIFIED vs INFERRED, open questions.
