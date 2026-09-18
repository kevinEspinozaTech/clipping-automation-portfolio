# 06 — Roadmap

> This roadmap replaces the Stage 1 clipping roadmap following the pivot documented in [`decisions/ADR-001-pivot-to-original-faceless-content.md`](decisions/ADR-001-pivot-to-original-faceless-content.md).

## Current focus: first real automation

Per the project's current priorities, the **first real automation to be built** concentrates narrowly on the early-pipeline stages, before any production work:

| Focus area | Scope | Status |
|---|---|---|
| Research | Capturing real, sourced signals for candidate topics (Wikipedia, Eurostat, etc.). | **Stage 2 — done for the initial idea list** |
| Idea bank | Logging candidate topics in `topic-registry.csv`. | **Stage 2 — done, 5 real topics seeded** |
| Topic scoring | Applying the 7-dimension model in [`prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md) and [`07-topic-scoring-methodology.md`](07-topic-scoring-methodology.md), logged in `topic-scoring-log.csv`. | **Stage 2 — methodology + initial scoring done** |
| Blocking rule | Hard-block a topic when sources or visual resources are `INSUFFICIENT`, independent of score. | **Stage 2 — documented + modeled in n8n** |
| Source documentation | Logging and verifying factual sources in `source-registry.csv` before any script work begins. | Next — human verification of Stage 2's sourced topics |
| Assisted script drafting | Applying [`prompts/script-draft-assist-prompt.md`](../prompts/script-draft-assist-prompt.md), always followed by mandatory human review. | Not started |
| State logging | Keeping `status` fields in the registries accurate as topics move through the pipeline. | Ongoing |

Stage 2 deliberately stops at scoring: every seeded topic sits at `status = PENDING_HUMAN_REVIEW` because `sources_available_status` and `visual_resources_feasible_status` require a human to confirm them — the AI-assisted research surfaced real, cited evidence but never self-promotes a topic to `CONFIRMED`/`recommended`.

## Explicitly out of scope for now

Per current project constraints, the following are **not** implemented yet and are not part of the next build increment:

- Automatic/unattended publishing of any kind.
- Downloading third-party videos.
- Mass or bulk content generation.
- Real, paid API calls (AI, TTS, stock libraries, publishing APIs).
- Storing large video/audio files in this Git repository.

## Full pipeline status

| Pipeline stage | Status |
|---|---|
| Research, idea bank, topic scoring | **In progress (Stage 2)** — see above |
| Source verification | Next — human verification of Stage 2's sourced topics |
| Visual-license verification | Governance + n8n demo gate exist (`visual-asset-rights-gate.json`); not yet wired to real registries |
| Script creation + human review | Prompt defined; not yet automated |
| Narration | Planned |
| Maps, graphics & authorized material sourcing | Planned |
| Long-form video edit | Planned |
| Shorts derivation | Prompt defined ([`prompts/shorts-segment-scoring-prompt.md`](../prompts/shorts-segment-scoring-prompt.md)); not yet automated |
| Subtitles | Planned |
| Final human review | Checklist only ([`tests/validation-checklist.md`](../tests/validation-checklist.md)) |
| Private/draft upload & manual publish | Planned; always manual by design |
| Metrics & continuous improvement | Registry skeleton exists (`performance-metrics.csv`); not yet automated |

## Guiding principles for every future stage

- No stage may weaken or bypass the visual-asset license gate in [`03-visual-asset-rights-policy.md`](03-visual-asset-rights-policy.md).
- No stage may introduce automatic publishing without an explicit, separate decision to do so.
- No stage may copy scripts, thumbnails, or videos from other channels.
- Growth in scale (more videos, more automation) only follows after the MVP (3 long-form videos, 9-12 Shorts, 6 weeks — see [`05-mvp-testing-plan.md`](05-mvp-testing-plan.md)) has been produced and reviewed under full human supervision.
