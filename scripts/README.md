# Scripts

## Stage 1 status

No executable scripts exist yet. This folder is a placeholder for automation introduced in later stages.

## Planned contents (future stages)

| Stage | Script (planned) | Purpose |
|---|---|---|
| 3 | Transcription runner | Send audio from `VERIFIED` sources to a transcription service and store the result in a git-ignored location. |
| 6 | Clip generation | Python orchestration around FFmpeg to cut, crop/reformat to vertical, and render approved segments. |
| 8 | Publishing helper | Push approved, human-reviewed clips to authorized platforms via their APIs. |
| 9 | Metrics collector | Pull post-publish metrics into `templates/performance-metrics.csv` (or its production equivalent). |

## Constraints for any future script

- Must never process a source unless its `rights_status = VERIFIED` and all advancement conditions in [`../docs/03-content-rights-policy.md`](../docs/03-content-rights-policy.md) are met.
- Must never write real media files, transcripts, or credentials into version control (see `../.gitignore`).
- Must never auto-publish without a recorded human approval.
