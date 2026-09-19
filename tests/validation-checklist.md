# Validation Checklist

Manual checklist executed before every commit to this repository. See [`../docs/05-mvp-testing-plan.md`](../docs/05-mvp-testing-plan.md) for the broader testing plan across all stages.

## Repository hygiene

- [ ] `git status` reviewed; only intended files are staged.
- [ ] Full diff reviewed before commit.
- [ ] No changes made outside this project's own files.

## CSV integrity

- [ ] `topic-registry.csv`, `topic-scoring-log.csv`, `source-registry.csv`, `visual-asset-registry.csv`, `performance-metrics.csv`, `results/sample-results.csv`, `channel-video-registry.csv`, `niche-scoring-matrix.csv`, and `niche-format-comparison.csv` all have consistent headers.
- [ ] Every `topic_id` referenced in `topic-scoring-log.csv` exists in `topic-registry.csv` (no orphan rows).
- [ ] No `final_score` in `topic-registry.csv` is a number unsupported by measured rows in `topic-scoring-log.csv` (see [`../docs/07-topic-scoring-methodology.md`](../docs/07-topic-scoring-methodology.md)).
- [ ] Every `niche_id` referenced in `niche-scoring-matrix.csv` exists in `niche-format-comparison.csv` (no orphan rows).
- [ ] No `total_score` in `niche-format-comparison.csv` is a number unsupported by measured rows in `niche-scoring-matrix.csv` (see [`../docs/09-niche-scoring-methodology.md`](../docs/09-niche-scoring-methodology.md)).
- [ ] No view/subscriber figure in `channel-video-registry.csv` is a fabricated-looking number — every such field is either a real cited figure or `NOT_PUBLICLY_AVAILABLE`.
- [ ] Every row has the same number of columns as its header.
- [ ] All data rows are clearly fictitious/example data.

## n8n workflows

- [ ] `n8n/stage-01-topic-research-pipeline.json` and `n8n/visual-asset-rights-gate.json` both parse as valid JSON.
- [ ] No credentials, API keys, or real instance identifiers are present in either file.
- [ ] Only standard (non-community) n8n node types are used.

## Secrets and sensitive data

- [ ] No API keys, tokens, passwords, or `.env` files are present.
- [ ] No real emails, contracts, license evidence, or personal data are present.
- [ ] No unnecessary personal file paths are present.
- [ ] `private/` contains only its own `README.md`.

## Protected content

- [ ] No video, audio, narration, or transcript files are tracked.
- [ ] No real license/permission evidence is tracked.
- [ ] No script, thumbnail, or footage copied from another channel is present.

## Documentation

- [ ] Relative Markdown links resolve to existing files.
- [ ] README accurately reflects current status and does not overclaim working automation.

## Result log

Record the outcome of each run of this checklist here (append, do not overwrite):

| Date | Result | Notes |
|---|---|---|
| 2026-09-18 | Pass | Initial Stage 1 commit (clipping-focused) — see prior entry in project history. |
| 2026-09-18 | Pass | Pivot commit (original faceless content) — all checks above executed manually; see final report in the pull request description. |
