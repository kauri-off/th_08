# IMPL93 — effect drawing: billboard vectors, converge angle, ring z (visible CODE BUGs) — local task

Source: `specs/changelog/answers_re_q33.md` §3 items 1–3, 6; `answers_re_q32.md` §3 item 7. Implement from the cited
numbered-spec sections only; spec-ref comments per `CLAUDE.md`; follow `docs/PARITY_POLICY.md`; unit-test what can be
tested without game data. Open details: one-line `// SPEC-GAP:` plus a question in `docs/briefs/IMPL93_QUESTIONS.md`.

## Deliverables

1. **List-B/C billboards** (13 §2.6c, 06 §10.1): right vector = normalise(cross(facing, up)) of the stage camera,
   written only when `Stage_SetCamera` runs (keep the old value while the stage layers are skipped); half size =
   ((len·0.5)·sprite_w)·scale.x with len the 3D length. The D3DX SSE projection arithmetic is optional (no visible effect).
2. **Converge effects** (13 §2.6, types 17 / 18 / 27): `EffInit_Converge` angle = random(2π) − π.
3. **Ring effects** (13 §2.5): ring vertices at z 0.

All session numbers must stay full (golden 25634, fullrun_noclip 124707, selftest1 1922, demos 0–3). Report the golden
draw summary line before and after, plus the etama.anm#1 / #2 group lines.
