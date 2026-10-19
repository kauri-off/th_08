# RE: NOCLIP session recording

Goal: the user records a full run of the original with the player unable to die, and the port replays it in sync.

Deliverables:
1. `re/tools/record_session.sh --noclip` and `play_session.sh` (automatic when the session's meta says so): the probe makes `Player_Die` return at exactly the point the port's `debug_invuln` does (after ScrambleDecoys and the hit counter, at the "player state != 0" check, as if state were non-zero). Nothing else changes: graze, items, bombs, deathbomb window logic untouched. Write `noclip: 1` into `meta.txt`.
2. Verify: record a short noclip session under Xvfb that takes hits, play it back, `session.py compare` bit-exact. Confirm in `specs/09_player.md` (§6.1) which work happens before that check, so the port's early return is placed identically; fix the spec if not.
3. Document the flag in `specs/data/drawlog/README.md` "Sessions" and `sessions/README.md`, and give the user the exact command for a full-run recording.
