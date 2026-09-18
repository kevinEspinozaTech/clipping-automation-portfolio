# Stage 1 Validation Checklist

Manual checklist executed before every commit to this repository at this stage. See [`../docs/05-mvp-testing-plan.md`](../docs/05-mvp-testing-plan.md) for the broader testing plan across all stages.

## Repository hygiene

- [ ] `git status` reviewed; only intended files are staged.
- [ ] Full diff reviewed before commit.
- [ ] No changes made outside this project's own files (or the minimal necessary root files in this dedicated repository).

## CSV integrity

- [ ] `content-registry.csv`, `rights-registry.csv`, `performance-metrics.csv`, and `results/sample-results.csv` all have consistent headers.
- [ ] Every row has the same number of columns as its header.
- [ ] All data rows are clearly fictitious/example data.

## n8n workflow

- [ ] `n8n/stage-01-content-intake.json` parses as valid JSON.
- [ ] No credentials, API keys, or real instance identifiers are present in the file.
- [ ] Only standard (non-community) n8n node types are used.

## Secrets and sensitive data

- [ ] No API keys, tokens, passwords, or `.env` files are present.
- [ ] No real emails, contracts, permission evidence, or personal data are present.
- [ ] No unnecessary personal file paths are present.
- [ ] `private/` contains only its own `README.md`.

## Protected content

- [ ] No video, audio, or transcript files are tracked.
- [ ] No real evidence of rights agreements is tracked.

## Documentation

- [ ] Relative Markdown links resolve to existing files.
- [ ] README accurately reflects current status (Stage 1 only — no working automation claimed).

## Result log

Record the outcome of each run of this checklist here (append, do not overwrite):

| Date | Result | Notes |
|---|---|---|
| 2026-09-18 | Pass | Initial Stage 1 commit — all checks above executed manually; see final report in the pull request description. |
