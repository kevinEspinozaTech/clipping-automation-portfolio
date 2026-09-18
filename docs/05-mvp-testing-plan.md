# 05 — MVP Testing Plan

## Purpose

Define how each stage of this system will be validated before it is considered reliable enough to touch real production. This document also defines the MVP scope itself.

## MVP definition

The first version of this system is a **semi-automated MVP**, not a fully autonomous pipeline:

- **Output:** 3 Spanish-language long-form videos, plus 9-12 Shorts derived from them (own content only).
- **Timeline:** estimated 6 weeks.
- **Publishing:** every publish action requires explicit human approval. There is no automatic publishing path.
- **Scale:** no mass production — the MVP intentionally stays small and human-supervised.
- **Content originality:** no copying of scripts, thumbnails, or videos from other channels, at any point.

## Structural validation (applies now)

See [`../tests/validation-checklist.md`](../tests/validation-checklist.md) for the concrete checklist executed for each commit. In summary:

- All CSV registries have consistent headers and equal column counts per row.
- All CSV example data is clearly fictitious.
- Both n8n workflow JSON files are valid and importable.
- No secrets, credentials, real evidence, or personal data are present anywhere in the tracked repository.
- No media, narration, or private files are tracked.
- Relative Markdown links resolve correctly.

## Functional validation (planned, by pipeline stage)

| Stage | What must be tested before it ships |
|---|---|
| Research / idea bank / scoring | Topic scoring logic correctly computes `final_score` and only marks topics `recommended` at/above the 6.0 threshold; no topic can reach `SCRIPT_DRAFT` status without documented sources. |
| Source verification | No source can be cited in a script draft unless it has a corresponding, human-verified row in `source-registry.csv`. |
| Visual-license verification | No asset can be marked usable without all 8 mandatory fields populated, `approval_status = VERIFIED`, `license_type != UNAUTHORIZED`, and `human_review_completed = TRUE`. |
| Script drafting | Draft output is cross-checked against `sources_used` to confirm every citation is real and verified; `unsupported_claims_flagged` items are resolved before narration. |
| Narration / edit / Shorts / subtitles | Not yet in scope for testing — not implemented. |
| Human review | No video reaches the publishing stage without an explicit, recorded human approval at both the script-review and final-review checkpoints. |
| Publishing | Publishing is always a manual human action; the system never calls a publish API automatically. |
| Metrics | Metrics ingestion is validated against platform sample data before being trusted for reporting. |

## Test data policy

All test data used to validate this system is fictitious, synthetic, or explicitly owned by the developer. Real third-party scripts, thumbnails, or videos are never used for testing — edge cases are simulated with fabricated registry rows instead.
