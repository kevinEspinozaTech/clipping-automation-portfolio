# 05 — MVP Testing Plan

## Purpose

Define how each stage of this system will be validated before it is considered reliable enough to touch real content. Stage 1 has no automation to test functionally; this document establishes the plan future stages must follow, and the structural checks that do apply now.

## Stage 1 — structural validation (applies now)

See [`tests/validation-checklist.md`](../tests/validation-checklist.md) for the concrete checklist executed for this stage. In summary:

- All CSV registries have consistent headers and equal column counts per row.
- All CSV example data is clearly fictitious.
- The n8n workflow JSON is valid and importable.
- No secrets, credentials, real evidence, or personal data are present anywhere in the tracked repository.
- No media files (video/audio) or private files are tracked.
- Relative Markdown links resolve correctly.

## Stage 2+ — functional validation (planned)

| Stage | What must be tested before it ships |
|---|---|
| 2 — Intake automation | Rights-gate logic correctly blocks any source missing one or more required flags; no source can reach `READY_FOR_TRANSCRIPTION` without all six advancement conditions met. |
| 3 — Transcription | Transcription only triggers for sources with `processing_status = READY_FOR_TRANSCRIPTION`; transcripts are stored only in git-ignored locations. |
| 4–5 — AI scoring | Prompt output validated against the documented JSON schema; any `rights_risk_flag = true` output is confirmed to force human review rather than being silently ignored. |
| 6 — Clip generation | Generated clips match source segment boundaries; FFmpeg commands are tested against known-safe sample inputs (never real unauthorized source video). |
| 7 — Human review | No clip reaches the publishing stage without an explicit, recorded human approval. |
| 8 — Publishing | Publishing target platform is cross-checked against `allowed_platforms` in the rights registry before every publish action. |
| 9 — Metrics | Metrics ingestion is validated against platform API sample responses before being trusted for reporting. |

## Test data policy

All test data used to validate this system — at every stage — must be fictitious, synthetic, or explicitly owned by the developer. Real third-party source content is never used for testing rights-gate logic; edge cases are simulated with fabricated registry rows instead.
