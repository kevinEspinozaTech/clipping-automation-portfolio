# Scripts

## Current status

No executable scripts exist yet. This folder is a placeholder for automation introduced in later stages, per [`../docs/06-roadmap.md`](../docs/06-roadmap.md).

## Planned contents (future stages)

| Stage | Script (planned) | Purpose |
|---|---|---|
| Research automation | Topic scoring runner | Apply [`../prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md) and write results into `topic-registry.csv`. |
| Research automation | Script draft runner | Apply [`../prompts/script-draft-assist-prompt.md`](../prompts/script-draft-assist-prompt.md) against verified sources from `source-registry.csv`. |
| Production | Narration (TTS) helper | Generate narration audio from an approved script. |
| Production | Map/graphic generation helper | Produce original maps and charts from open geodata/statistics. |
| Production | Long-form edit assembly | Python + FFmpeg assembly of narration, visuals, and cleared assets into the long-form video. |
| Production | Shorts derivation | Cut Shorts from the project's own long-form video using [`../prompts/shorts-segment-scoring-prompt.md`](../prompts/shorts-segment-scoring-prompt.md). |
| Production | Subtitle generation | Generate subtitles for both long-form videos and Shorts. |
| Publishing | Metrics collector | Pull post-publish metrics into `templates/performance-metrics.csv` (or its production equivalent). |

## Constraints for any future script

- Must never use a visual/audio asset unless `approval_status = VERIFIED` and all advancement conditions in [`../docs/03-visual-asset-rights-policy.md`](../docs/03-visual-asset-rights-policy.md) are met.
- Must never write real media files, narration audio, or credentials into version control (see `../.gitignore`).
- Must never auto-publish without a recorded human approval — see the MVP constraints in [`../docs/05-mvp-testing-plan.md`](../docs/05-mvp-testing-plan.md) (no auto-publish, no mass production).
- Must never copy or closely paraphrase another channel's script, thumbnail, or video.
