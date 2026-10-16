# Clean-room brief — Phase 3: bullets, items, player

Same role and rules as before (TASK_TEMPLATE.md, RE_WORKFLOW.md). Continue in your SPEC_DIR: re-read NOTES.md
(especially "For later phases"), symbols.csv, structs.md and specs 00–07 first.

Describe behaviour per frame (order of operations, units, int vs float, rounding, RNG use) so the implementer can
reproduce gameplay frame-exactly. Struct tables, opcode/command tables, short pseudocode; never paste decompiled code.

Deliverables (ONLY these three; finish and verify one before the next):
1. `08_bullets_items.md` — bullet manager: struct, capacities, spawn from ECL (link to 07 aim modes), sprite/colour
   selection from etama.anm, motion and the bullet "extra commands" (ECL op 111 internals), wall/bounce rules,
   graze (radius, cooldown, score), hitbox per bullet type, cancel/clear (to items/points), lasers (all kinds, fields,
   collision shape), items (types, spawn velocity, gravity, auto-collect line and conditions, magnet radius, values,
   point/time-orb scoring as far as the code shows).
2. `09_player.md` — player struct, movement (speeds focused/unfocused, diagonal normalisation, bounds), hitbox and
   graze box, input bitmask mapping, shot types per character/team (.sht format fully), options/familiars, bombs
   (per character: duration, invulnerability, damage), death and deathbomb window, respawn/invulnerability, lives/
   bombs/power rules, the player mode byte at 0x17D5EF8+5, player-side damage/hit-test functions.
3. Answers to the implementer questions in `/home/anon/Projects/th_08/docs/QUESTIONS.md` (read ONLY that file in docs/):
   put each answer into the relevant existing spec (00/05/06) and list them in a short `answers_phase3.md`
   (question → answer → spec section). Skip questions that belong to MSG/RNG/menus (10/11) — note them as deferred.

Tools: extend your tools so that .sht files parse with 0 problems, and verify any table you read from the exe.
Finish with: produced files, what is VERIFIED vs INFERRED, open questions.
