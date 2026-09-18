# n8n Workflows

Two safe, non-functional demonstration workflows model the current pipeline. Neither calls any external service, requires credentials, or publishes anything. See [`../docs/decisions/ADR-001-pivot-to-original-faceless-content.md`](../docs/decisions/ADR-001-pivot-to-original-faceless-content.md) for why the pipeline changed from clipping to original content.

## 1. `stage-01-topic-research-pipeline.json`

### Purpose

Demonstrates the **Stage 2 scoring model**: research → idea bank → the two hard blocking gates → 7-dimension scoring → the recommendation gate → state logging (see [`../docs/06-roadmap.md`](../docs/06-roadmap.md) and [`../docs/07-topic-scoring-methodology.md`](../docs/07-topic-scoring-methodology.md)). Mirrors [`../prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md)'s 7-dimension model, computing `final_score` only from whichever dimensions are real numbers (never fabricating a value for a `NOT_MEASURED` one) in place of a real AI call.

### Manual test

1. Import the file into n8n (**Workflows → Import from File**).
2. Execute the workflow via the Manual Trigger.
3. Inspect **Execution Summary** for the final `status`, `final_score`, and `recommended`.
4. Edit **Set Fictitious Topic Data** to exercise other branches:
   - Set `sources_available_status` to `INSUFFICIENT` → expect `BLOCKED_NO_SOURCES` (checked before scoring, regardless of score).
   - Set `visual_resources_feasible_status` to `INSUFFICIENT` → expect `BLOCKED_NO_VISUAL_RIGHTS`.
   - Reduce the number of numeric score fields below 4 (turn more of them into the string `NOT_MEASURED`) → expect `final_score = REQUIRES_MANUAL_REVIEW`, routed to `PENDING_HUMAN_REVIEW`.
   - Lower the measured scores so their average falls below 6.0 → expect `PENDING_HUMAN_REVIEW`.
   - Set **both** `sources_available_status` and `visual_resources_feasible_status` to `CONFIRMED` (with a measured average ≥ 6.0) → expect `SOURCES_VERIFIED`, `recommended = true`. The demo data ships with both gates at `REQUIRES_MANUAL_REVIEW` on purpose, so a default run never self-approves.
   - Clear `topic_id`, `working_title`, or `category` → expect `BLOCKED_INVALID_INTAKE`.

## 2. `visual-asset-rights-gate.json`

### Purpose

Demonstrates the license gate from [`../docs/03-visual-asset-rights-policy.md`](../docs/03-visual-asset-rights-policy.md): an asset may only be marked usable if all 8 mandatory fields are present, `license_type` is not `UNAUTHORIZED`, `approval_status = VERIFIED`, and `human_review_completed = TRUE`. This gate is independent of, and runs after, the topic-research pipeline above — it applies once a topic has a script and needs supporting maps/footage/photos/music.

### Manual test

1. Import the file into n8n.
2. Execute via the Manual Trigger.
3. Inspect **Execution Summary** for the final `usage_status`.
4. Edit **Set Fictitious Asset Data** to exercise other branches:
   - Clear `source`, `author`, `verified_at`, `allowed_scope`, or `evidence_reference` → expect `BLOCKED_INCOMPLETE_RECORD`.
   - Set `license_type` to `UNAUTHORIZED` → expect `REJECTED_UNAUTHORIZED`.
   - Set `approval_status` to anything other than `VERIFIED` → expect `PENDING_REVIEW`.
   - Set `human_review_completed` to `false` → expect `PENDING_REVIEW`.
   - Otherwise → expect `CLEARED_FOR_USE`.

## Requirements (both workflows)

- A local or cloud n8n instance. No specific version is required to *read* the JSON — see [Limitations](#limitations).
- No community nodes. Only standard n8n nodes are used: `Manual Trigger`, `Set`, `If`, `Sticky Note`.
- No credentials of any kind are needed to import or run either workflow.

## Sample data

All data in both **Set** nodes is fictitious (`TOPIC-DEMO-0001`, `ASSET-DEMO-0001`, `example.com`). It does not reference any real topic, video, or asset.

## Expected results

| Workflow | Scenario | Output field |
|---|---|---|
| Topic research | Score ≥ 6.0 and both gates `CONFIRMED` | `status = SOURCES_VERIFIED`, `recommended = true` |
| Topic research | Score < 6.0, unmeasured, or gates not both `CONFIRMED` | `status = PENDING_HUMAN_REVIEW`, `recommended = false` |
| Topic research | `sources_available_status = INSUFFICIENT` | `status = BLOCKED_NO_SOURCES` |
| Topic research | `visual_resources_feasible_status = INSUFFICIENT` | `status = BLOCKED_NO_VISUAL_RIGHTS` |
| Topic research | Missing required field | `status = BLOCKED_INVALID_INTAKE` |
| Asset rights gate | All conditions pass | `usage_status = CLEARED_FOR_USE` |
| Asset rights gate | `license_type = UNAUTHORIZED` | `usage_status = REJECTED_UNAUTHORIZED` |
| Asset rights gate | Not yet `VERIFIED` or no human review | `usage_status = PENDING_REVIEW` |
| Asset rights gate | Missing mandatory field | `usage_status = BLOCKED_INCOMPLETE_RECORD` |

## Limitations

- Both workflows have been validated as **syntactically valid JSON** in the standard n8n export shape, but neither has been executed against a specific pinned n8n version in this environment. If your instance uses different node `typeVersion`s, n8n's import process should map or auto-upgrade them, but minor manual adjustment may be required.
- Neither workflow reads from or writes to the actual CSV registries — that integration is planned for a future automation stage.
- Neither calls any AI, research, or publishing service; the scoring formula in the topic-research pipeline (mean of measured dimensions, per [`../docs/07-topic-scoring-methodology.md`](../docs/07-topic-scoring-methodology.md)) runs as a plain n8n expression rather than a real AI call.
- The demo data ships with both gate fields at `REQUIRES_MANUAL_REVIEW`, so importing and running the workflow as-is never produces `SOURCES_VERIFIED` — that is intentional, not a bug: only a human editing the fields (or, later, a real human-review step) can set a gate to `CONFIRMED`.

## Future steps

- Connect **Set Fictitious Topic Data** to a real intake source (the `topic-registry.csv`/`topic-scoring-log.csv` files) and replace the hardcoded scores with a real call using [`../prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md).
- Connect the `SOURCES_VERIFIED` branch to a real assisted-drafting step using [`../prompts/script-draft-assist-prompt.md`](../prompts/script-draft-assist-prompt.md).
- Connect the visual-asset gate to `visual-asset-registry.csv` so `CLEARED_FOR_USE` assets are tracked per video before editing begins.
- Write results back to the registries instead of only summarizing them in-memory.
