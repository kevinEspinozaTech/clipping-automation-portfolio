# n8n Workflows

Two safe, non-functional demonstration workflows model the current pipeline. Neither calls any external service, requires credentials, or publishes anything. See [`../docs/decisions/ADR-001-pivot-to-original-faceless-content.md`](../docs/decisions/ADR-001-pivot-to-original-faceless-content.md) for why the pipeline changed from clipping to original content.

## 1. `stage-01-topic-research-pipeline.json`

### Purpose

Demonstrates the **first real automation target**: research → idea bank → topic scoring → source documentation gate → assisted script draft readiness → state logging (see [`../docs/06-roadmap.md`](../docs/06-roadmap.md)). Mirrors [`../prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md)'s scoring logic with a hardcoded average in place of a real AI call.

### Manual test

1. Import the file into n8n (**Workflows → Import from File**).
2. Execute the workflow via the Manual Trigger.
3. Inspect **Execution Summary** for the final `status`.
4. Edit **Set Fictitious Topic Data** to exercise other branches:
   - Lower any of the four scores so their average falls below 6.0 → expect `IDEA_BACKLOG`.
   - Set `sources_documented` to `false` or `source_count` to `0` → expect `SOURCES_PENDING`.
   - Clear `topic_id`, `working_title`, or `category` → expect `BLOCKED_INVALID_INTAKE`.
   - Otherwise → expect `SCRIPT_DRAFT_READY`.

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
| Topic research | All conditions pass | `status = SCRIPT_DRAFT_READY` |
| Topic research | `final_score` < 6.0 | `status = IDEA_BACKLOG` |
| Topic research | No sources documented | `status = SOURCES_PENDING` |
| Topic research | Missing required field | `status = BLOCKED_INVALID_INTAKE` |
| Asset rights gate | All conditions pass | `usage_status = CLEARED_FOR_USE` |
| Asset rights gate | `license_type = UNAUTHORIZED` | `usage_status = REJECTED_UNAUTHORIZED` |
| Asset rights gate | Not yet `VERIFIED` or no human review | `usage_status = PENDING_REVIEW` |
| Asset rights gate | Missing mandatory field | `usage_status = BLOCKED_INCOMPLETE_RECORD` |

## Limitations

- Both workflows have been validated as **syntactically valid JSON** in the standard n8n export shape, but neither has been executed against a specific pinned n8n version in this environment. If your instance uses different node `typeVersion`s, n8n's import process should map or auto-upgrade them, but minor manual adjustment may be required.
- Neither workflow reads from or writes to the actual CSV registries — that integration is planned for a future automation stage.
- Neither calls any AI, research, or publishing service; the scoring math in the topic-research pipeline is a placeholder for a future AI step.

## Future steps

- Connect **Set Fictitious Topic Data** to a real intake source (form, spreadsheet, or the `topic-registry.csv`/`source-registry.csv` files) and replace the hardcoded score computation with a real call using [`../prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md).
- Connect the `SCRIPT_DRAFT_READY` branch to a real assisted-drafting step using [`../prompts/script-draft-assist-prompt.md`](../prompts/script-draft-assist-prompt.md).
- Connect the visual-asset gate to `visual-asset-registry.csv` so `CLEARED_FOR_USE` assets are tracked per video before editing begins.
- Write results back to the registries instead of only summarizing them in-memory.
