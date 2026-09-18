# 06 — Roadmap

> This roadmap replaces the Stage 1 clipping roadmap following the pivot documented in [`decisions/ADR-001-pivot-to-original-faceless-content.md`](decisions/ADR-001-pivot-to-original-faceless-content.md).

## Current focus: first real automation

Per the project's current priorities, the **first real automation to be built** concentrates narrowly on the early-pipeline stages, before any production work:

| Focus area | Scope |
|---|---|
| Research | Capturing trend/competition signals for candidate topics. |
| Idea bank | Logging candidate topics in `topic-registry.csv`. |
| Topic scoring | Applying [`prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md) to prioritize the idea bank. |
| Source documentation | Logging and verifying factual sources in `source-registry.csv` before any script work begins. |
| Assisted script drafting | Applying [`prompts/script-draft-assist-prompt.md`](../prompts/script-draft-assist-prompt.md), always followed by mandatory human review. |
| State logging | Keeping `status` fields in the registries accurate as topics move through the pipeline. |

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
| Research, idea bank, topic scoring | **Next automation target** — see above |
| Source verification | **Next automation target** — see above |
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
