# RE-Q29 — next divergences after RE-Q28, open implementer questions

Read `docs/briefs/RE_WORKFLOW.md` first. Same rules as RE-Q28: answers into the numbered specs, changelog
`specs/changelog/answers_re_q29.md` with SPEC FIXED / CODE BUG / NEW FACT labels and the CODE BUG list at the end.
Never edit `src/`. RE-Q28 fixes A–K are being implemented (impl42–45); keep using a scratch port with them applied
(`re/work/runs/q29/portfix/`, refreshed from the current `src/`).

## Questions

1. Next first divergences with A–K applied: golden 10707 (score), fullrun_noclip 9408 (GameFlags bit 7), demo 0 5246
   (score +1), demo 1 4155, demo 2 4660, demo 3 6684. Root-cause each, confirm on the scratch port, give after-fix
   numbers.
2. Answer the open questions in `docs/briefs/IMPL35_QUESTIONS.md` … `IMPL40_QUESTIONS.md` (only those not already
   answered by RE-Q27/Q28) in the numbered specs.

Run the port with `TH08_INVULN=off` (or an isolated `XDG_CONFIG_HOME`) until impl42 lands: the user's port.cfg may set
`invuln = on`.
