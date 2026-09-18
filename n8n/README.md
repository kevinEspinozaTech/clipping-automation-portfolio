# n8n Workflow — Stage 1: Content Intake and Rights Gate (Demo)

## Purpose

`stage-01-content-intake.json` is a **safe, non-functional demonstration** of the rights-gate logic defined in [`../docs/03-content-rights-policy.md`](../docs/03-content-rights-policy.md). It shows how a source video's fictitious metadata is validated, checked against `rights_status` and usage flags, and routed to one of three outcomes: `READY_FOR_TRANSCRIPTION`, `HUMAN_REVIEW_REQUIRED`, or `BLOCKED_RIGHTS` / `BLOCKED_INVALID_INTAKE`.

It does not call any external service, does not require credentials, and does not publish or transcribe anything.

## Requirements

- A local or cloud n8n instance (self-hosted or n8n.cloud). No specific version is required to *read* the JSON, but see [Limitations](#limitations) regarding import compatibility.
- No community nodes. Only standard n8n nodes are used: `Manual Trigger`, `Set`, `If`, and `Sticky Note`.
- No credentials of any kind are needed to import or run this workflow.

## Importing

1. Open your n8n instance.
2. Go to **Workflows → Import from File** (or **⋯ menu → Import from File** depending on your n8n version).
3. Select `stage-01-content-intake.json`.
4. The workflow will appear with its nodes, connections, and sticky notes intact.

## Manual test

1. Open the imported workflow.
2. Click **Execute Workflow** (the Manual Trigger will fire).
3. Inspect the output of the **Execution Summary** node — it prints a one-line summary combining `source_id`, `processing_status`, and the block reason (if any).
4. To exercise other branches, open **Set Fictitious Source Data** and change values, then re-execute:
   - Set `rights_status` to something other than `VERIFIED` (e.g., `PENDING_REVIEW`) → expect `BLOCKED_RIGHTS`.
   - Set any of `commercial_use_allowed`, `editing_allowed`, `platform_use_allowed` to `false`, or `authorization_expired` to `true` → expect `HUMAN_REVIEW_REQUIRED`.
   - Set `human_review_completed` to `false` → expect `HUMAN_REVIEW_REQUIRED`.
   - Clear `source_id`, `source_platform`, `creator_name`, or `rights_status` → expect `BLOCKED_INVALID_INTAKE`.

## Sample data

All data in the **Set Fictitious Source Data** node is fictitious (`SRC-DEMO-0001`, `Demo Creator`, `https://example.com/demo-source`). It does not reference any real content, creator, or platform account.

## Expected results

| Scenario | `processing_status` output |
|---|---|
| All conditions pass | `READY_FOR_TRANSCRIPTION` |
| `rights_status` ≠ `VERIFIED` | `BLOCKED_RIGHTS` |
| Any usage flag false or expired = true | `HUMAN_REVIEW_REQUIRED` |
| `human_review_completed` = false | `HUMAN_REVIEW_REQUIRED` |
| Missing required intake field | `BLOCKED_INVALID_INTAKE` |

## Limitations

- This workflow has been validated as **syntactically valid JSON** and structured according to the standard n8n workflow export shape, but it has not been executed against a specific pinned n8n version in this environment. Node `typeVersion` values reflect commonly available versions at the time of writing; if your instance uses different versions, n8n's import process should still map or auto-upgrade them, but minor manual adjustment may be required.
- It does not read from or write to `content-registry.csv` / `rights-registry.csv` — that integration is planned for Stage 2.
- It does not call any AI, transcription, or publishing service.

## Future steps

- Stage 2: replace the static `Set` node with a real trigger (e.g., form submission or spreadsheet read) sourced from `templates/content-registry.csv` and `templates/rights-registry.csv`.
- Stage 2: write the resulting `processing_status` back to the registry instead of only summarizing it in-memory.
- Stage 3+: connect the `READY_FOR_TRANSCRIPTION` branch to an actual transcription step.
