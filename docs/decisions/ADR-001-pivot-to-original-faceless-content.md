# ADR-001: Pivot from Third-Party Clipping to Original Faceless Content

- **Status:** Accepted
- **Date:** 2026-09-18
- **Supersedes:** The clipping-automation direction shipped in Stage 1 (PR #1, commit `bf27f88`)

## Context

Stage 1 of this project ("clipping-automation-portfolio") built the governance skeleton for a pipeline that would clip short-form vertical videos out of **third-party** long-form source videos, gated by a mandatory rights-verification process before any reuse. That stage delivered documentation, a content-rights policy, CSV registries, permission templates, AI prompts, and a demo n8n workflow — but no functional automation.

## The initial idea: clipping third-party content

The original plan was to identify existing long-form videos (streams, podcasts, gameplay, etc.) from other creators, verify commercial reuse rights, and — only for verified sources — transcribe, score, and cut short vertical clips for republishing.

## Risks identified

- **Copyright risk.** Even with a rights-verification gate, sourcing content that originates from someone else carries ongoing legal exposure: rights can be misrepresented, revoked, or contested after the fact, and enforcement (claims, takedowns, strikes) can happen regardless of the documentation on our side.
- **Reused-content risk for monetization.** Platforms increasingly restrict or demonetize channels built primarily on reused/repurposed third-party material, independent of whether reuse was technically authorized — this directly threatens the project's viability as a monetizable channel.
- **Operational fragility.** The entire pipeline's throughput was bottlenecked by how many creators would grant explicit, documented, commercial-use permission — a slow and uncertain external dependency.

## Decision

Pivot the project's core purpose to producing **original, faceless YouTube content in Spanish**, initially focused on European geography, infrastructure, cities, borders, and trivia. The system no longer reuses other creators' footage. Instead, it researches topics, drafts original scripts from verified factual sources, narrates them, and illustrates them with material whose license is explicitly verified per-asset (maps, stock footage, charts, music) — most of which will itself be original, owned, or public-domain/Creative-Commons-compatible rather than third-party video reuse.

**This is a strategic decision driven by risk and viability, not a reaction to a technical blocker.** The clipping approach was technically buildable; it was assessed as too risky and too fragile as a monetizable, sustainable channel strategy.

## What was preserved

- The core governance pattern: nothing advances through the pipeline without an explicit, human-reviewed verification record.
- The five-state approval lifecycle (`PENDING_REVIEW` / `VERIFIED` / `REJECTED` / `EXPIRED` / `REVOKED`), now applied to individual visual/audio assets instead of whole source videos.
- The permission-request template and authorization-checklist pattern, reworded for requesting/checking a single asset's license.
- The n8n workflow-skeleton pattern (Manual Trigger → Set → validation → gated branching → state output), now modeling two flows: the research-to-draft-script pipeline, and the visual-asset license gate.
- Secret hygiene and `.gitignore` rules — no media, credentials, or private evidence ever tracked in git.
- The human-in-the-loop philosophy: AI assists (scoring, drafting) but never makes a final rights or publishing decision.

## What was replaced

- `content-registry.csv` (source videos to clip) → `topic-registry.csv` (original video ideas / banco de ideas).
- `rights-registry.csv` (rights to reuse a creator's whole video) → `visual-asset-registry.csv` (per-asset license status, using a new 7-value license taxonomy: `ORIGINAL`, `OWN_MATERIAL`, `PUBLIC_DOMAIN`, `CREATIVE_COMMONS_COMPATIBLE`, `LICENSED`, `DIRECT_PERMISSION`, `UNAUTHORIZED`).
- The clip-scoring prompt (score third-party segments for clip potential) → repurposed to score which moments of the **user's own** long-form video work as Shorts.
- The n8n content-intake demo → repurposed into a research/idea-bank/scoring/source-documentation/script-draft pipeline demo, plus a new, separate visual-asset license-gate demo.
- The roadmap and MVP plan, now scoped to original-content production instead of clip generation.

## New architecture (summary)

```text
Research & trends -> Idea bank -> Topic scoring -> Source verification
  -> Visual-license verification -> Script creation -> Human script review
  -> Narration -> Maps/graphics/authorized material -> Long-form edit
  -> Shorts derivation -> Subtitles -> Final human review
  -> Private/draft upload -> Manual publish -> Metrics -> Continuous improvement
```

See [`../02-workflow-architecture.md`](../02-workflow-architecture.md) for the full diagram and component breakdown.

## Consequences

- All existing rights-related documentation and registries needed renaming and field changes to reflect "license of an asset used inside original work" rather than "rights to reuse someone else's whole work" — this is a one-time, deliberate breaking change to the Stage 1 schema, not an incremental extension of it.
- The MVP is redefined: 3 Spanish long-form videos and 9-12 derived Shorts over an estimated 6 weeks, entirely human-approved, with no automatic publishing and no mass production (see [`../05-mvp-testing-plan.md`](../05-mvp-testing-plan.md)).
- The first real automation to be built targets research, idea banking, topic scoring, source documentation, assisted script drafting, and state logging — not production or publishing (see [`../06-roadmap.md`](../06-roadmap.md)).
