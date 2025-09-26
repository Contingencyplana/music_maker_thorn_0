# Input Contract — music_maker_thorn_0

This maker loads artifacts from all seven builders and **validates** them rigorously.
Each file **must** declare a schema:

```json
{ "mtc_schema": "<domain>/<semver>" }
```

## Required / Optional Inputs

| Domain     | File                                | Required?   | Notes                                                   |
|------------|-------------------------------------|-------------|---------------------------------------------------------|
| rhythm     | exports/rhythm.json                 | Recommended | 16-step tracks, bpm, swing                              |
| melody     | exports/melody.json or melody.mid   | Optional    | JSON preferred early; MIDI supported                    |
| harmony    | exports/harmony.json                | Optional    | Progression + optional voice-leading hints              |
| form       | exports/form.json                   | Optional    | Sections with bar ranges & repeats                      |
| sound      | exports/instruments.json            | Optional    | Track → instrument/patch & synth params                 |
| expression | exports/expression.json             | Optional    | Velocity curves, swing %, articulations                 |
| mix        | exports/mix.json                    | Optional    | Track gains, pan, FX sends, scenes                      |

Thorn should run with partial inputs but will warn/error clearly on contract violations.

---

## Schemas (v1.0.0)

### rhythm/1.0.0

```json
{
  "mtc_schema": "rhythm/1.0.0",
  "bpm": 100,
  "time_signature": { "beats_per_bar": 4, "beat_unit": 4 },
  "swing_percent": 0,
  "tracks": [
    { "name": "kick", "steps": [0,1,0,0, 0,1,0,0, 0,1,0,0, 0,1,0,0] }
  ]
}
```

### melody/1.0.0 (JSON alt to MIDI)

```json
{
  "mtc_schema": "melody/1.0.0",
  "key": "C major",
  "notes": [
    { "t": 0, "dur": 1, "pitch": 60, "vel": 90 },
    { "t": 1, "dur": 1, "pitch": 62, "vel": 85 }
  ]
}
```

### harmony/1.0.0

```json
{
  "mtc_schema": "harmony/1.0.0",
  "key_center": "C",
  "mode": "ionian",
  "progression": ["C", "Am", "F", "G"],
  "voice_leading_hints": true
}
```

### form/1.0.0

```json
{
  "mtc_schema": "form/1.0.0",
  "sections": [
    { "name": "Intro", "bars": [1, 4] },
    { "name": "Verse", "bars": [5, 12] }
  ],
  "order": ["Intro", "Verse", "Verse"]
}
```

### instruments/1.0.0

```json
{
  "mtc_schema": "instruments/1.0.0",
  "tracks": [
    { "name": "kick", "preset": "drums/kick01" },
    { "name": "lead", "preset": "synths/saw_lead", "adsr": [0.01, 0.1, 0.8, 0.2] }
  ]
}
```

### expression/1.0.0

```json
{
  "mtc_schema": "expression/1.0.0",
  "swing_percent": 10,
  "velocity_curve": "gentle",
  "articulations": { "lead": "legato" }
}
```

### mix/1.0.0

```json
{
  "mtc_schema": "mix/1.0.0",
  "levels": { "kick": -3.0, "lead": -6.0 },
  "pan": { "kick": 0, "lead": -10 },
  "fx_sends": { "lead": { "reverb": 0.25 } }
}
```

## Validation Rules (MVP)

- Reject if `mtc_schema` is missing or domain mismatch.
- **Rhythm:** steps length must be 16; `time_signature` fields required.
- **Form:** all `order` items must exist in `sections`.
- **Melody:** if `.mid` provided, attempt parse; else fall back to JSON.
- For optional inputs, warn (don’t crash) when absent; degrade gracefully.
