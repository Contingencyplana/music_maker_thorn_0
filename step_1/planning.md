# Planning — music_maker_thorn_0\step_1

**Role:** First container layer for the challenging Music Maker (Thorn).
Frames the path toward runnable **challenge nodes**.

---

## Goals

- Establish the **trial/integrity path** for music making.
- Keep this layer as a container only (non-runnable).
- Direct work into branches (`step_1_*/`) where actual loaders, validators, and challenge engines will live.

---

## Roadmap

1. **Create pilot branch**
   - Add `step_1_1/` with its own `planning.md`.
   - Confirm cascade: `step_1/ → step_1_1/ → step_1_1_1/` (first runnable challenge node).

2. **Frame tone**
   - Challenges are constructive, not punitive.
   - Copy should guide with clear feedback: “Try again,” “Off-beat detected,” “Progression mismatch.”

3. **Pass requirements downstream**
   - Children must load builder exports, validate against schemas, compose a project state, and run at least one challenge.

---

## Sub-steps

- [ ] `step_1_1/` → **Branch A (Pilot Challenge Path)**
  - Leads to first runnable node (`step_1_1_1/`) with loader + validator + minimal trial engine.

- [ ] `step_1_2/` → **Branch B (Extended Trials)**
  - Additional timing/harmony challenges, stricter validators.

- [ ] `step_1_3/` → **Branch C (Experimental Paths)**
  - Alternative scoring models, advanced trials (e.g., polymetric accuracy).

> Runnable nodes live at depth **three**: `step_*_*_*/` (e.g., `step_1_1_1/`).

---

## Decisions

- 2025-09-29 — `step_1/` is a container only; no `story.md` or `code.py`.
- 2025-09-29 — Pilot challenge path set to `step_1_1_1/`.
- 2025-09-29 — Thorn tone defined: sharpening challenges with constructive feedback.
