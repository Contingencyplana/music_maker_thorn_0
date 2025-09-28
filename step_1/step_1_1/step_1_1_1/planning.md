# Planning — music_maker_thorn_0\step_1\step_1_1\step_1_1_1

**Role:** Runnable node for the challenging Music Maker (Thorn).
This is the **pilot challenge node**, where builder exports are loaded, validated, and tested through a minimal trial engine.

---

## Goals

- Implement a **loader + validator + minimal trial loop**.
- Load core builder artifacts (`rhythm.json`, `form.json`, `instruments.json`).
- Merge into `json/project.thorn.json` with metadata and initial `challenges[]`.
- Run at least one constructive trial (timing or form).
- Provide **feedback copy** in Thorn’s sharpening tone.

---

## Roadmap

1. **Scaffold node**
   - Add files:
     - `story.md` → Do–Ti challenge menu prompts
     - `code.py` → loaders, validators, trial logic
     - `json/` → runtime project state
     - `samples/` → starter artifacts
   - Ensure `planning.md` captures requirements and lessons learned.

2. **Implement loaders**
   - Load `rhythm.json`, `form.json`, and `instruments.json`.
   - Validate `"mtc_schema"` field and file structure.
   - Fail fast with constructive errors.

3. **Compose project state**
   - Export to `json/project.thorn.json`:
     ```json
     { "maker": "thorn", "version": "1.0.0", "created": "<iso>", "challenges": [] }
     ```

4. **Trial engine (minimal)**
   - Add timing or form challenge.
   - Record outcomes into `project["challenges"]`.
   - Display results with feedback copy.

5. **Playtest**
   - Run:
     ```powershell
     cd step_1\step_1_1\step_1_1_1
     python code.py
     ```
   - Confirm project saves and reloads.
   - Verify challenge feedback is constructive, not punitive.

---

## Sub-steps

- [ ] `story.md` → Do–Ti challenge menu (timing/form focus).
- [ ] `code.py` → loaders, validators, minimal trial engine.
- [ ] `json/project.thorn.json` → runtime state + challenge results.
- [ ] `samples/` → example builder exports for quick testing.

---

## Decisions

- 2025-09-29 — Established `step_1_1_1/` as the **pilot runnable node**.
- 2025-09-29 — Node must validate schema versions and record trial results.
- 2025-09-29 — Thorn tone confirmed: sharpening, constructive feedback.
