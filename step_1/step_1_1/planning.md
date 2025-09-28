# Planning — music_maker_thorn_0\step_1\step_1_1

**Role:** Intermediate container for the challenging Music Maker (Thorn).
Bridges the outer container (`step_1/`) and the runnable UI node (`step_1_1_1/`).

---

## Goals

- Act as a **transition layer**: not runnable itself, but sets up the pilot challenge node.
- Define scope, tone, and technical expectations for `step_1_1_1/`.
- Ensure all requirements for loader, validator, and trial engine are clearly passed downstream.

---

## Roadmap

1. **Scaffold pilot node**
   - Create `step_1_1_1/` with:
     - `planning.md`
     - `story.md` (Do–Ti menu tailored for challenges)
     - `code.py` (loader + validator + minimal trial engine)
     - `json/` (runtime project state)
     - `samples/` (starter artifacts)

2. **Define pilot requirements**
   - Load at minimum: `rhythm.json`, `form.json`, `instruments.json`.
   - Validate schema versions (`"mtc_schema": "<domain>/<semver>"`).
   - Export state to `json/project.thorn.json`.
   - Run a minimal challenge (timing or form).

3. **Tone alignment**
   - Copy should emphasize growth-through-trial.
   - Messages: “Good effort, check your timing,” “Progression mismatch detected, try again.”
   - Never punitive; always constructive.

---

## Sub-steps

- [ ] `step_1_1_1/` → **Pilot Node (Loader + Minimal Trial Engine)**
  - `planning.md` → detailed runnable scroll
  - `story.md` → Do–Ti challenge prompts
  - `code.py` → loaders, validators, simple trial logic
  - Outputs: `json/project.thorn.json`

- [ ] `step_1_1_2/` → **Extended Trial Node**
  - Adds stricter timing/harmony validators, more detailed scoring.

- [ ] `step_1_1_3/` → **Experimental Trial Node**
  - Explores alternative scoring models (e.g., polymetric accuracy, ghost-note challenges).

> Runnable challenge nodes live at this depth: `step_*_*_*/` (e.g., `step_1_1_1/`).

---

## Decisions

- 2025-09-29 — `step_1_1/` defined as structural bridge only.
- 2025-09-29 — Pilot node fixed at `step_1_1_1/` with loader + minimal trial engine.
- 2025-09-29 — Tone guidance: constructive feedback, sharpening trial path.
