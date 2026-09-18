# 01 — Business Case

> This document replaces the Stage 1 clipping business case. See [`decisions/ADR-001-pivot-to-original-faceless-content.md`](decisions/ADR-001-pivot-to-original-faceless-content.md) for the full rationale behind the pivot.

## Problem

Producing a consistent stream of original, well-researched video content is slow: it requires finding topics worth covering, verifying the facts behind them, writing an accurate script, narrating it, sourcing visuals that are actually cleared to use, editing, and deriving short-form content from the result — all before a single video can be published responsibly. Skipping the verification steps (facts, visual-asset licenses) is how channels end up with claims they can't back up or assets they can't legally use, even when the *content itself* is original.

## Opportunity

A "faceless" content format — narration over maps, graphics, and licensed/original visuals, with no on-camera talent — is well suited to automation-assisted production, and geography/infrastructure/trivia content about Europe has a durable, evergreen audience in Spanish-language markets. Building this with a rights-aware pipeline from the start (rather than bolting it on later) avoids repeating the risk profile that ended the original clipping approach (see ADR-001), while still capturing the benefits of automation for research, scoring, and drafting.

## Target outcome

A repeatable process where:

- Every published video is built from an original script, backed by documented, verifiable sources.
- Every supporting visual/audio asset has a documented, human-reviewed license before it appears in a published video.
- Publishing always requires human approval — no fully autonomous publish path exists.
- Early production (research, idea banking, scoring, source documentation, draft assistance) is automation-assisted, while script writing, narration quality, and final approval stay human-directed.

## Why this belongs in a portfolio

This project demonstrates:

- The ability to recognize and act on business/legal risk in an automation design, including reversing an earlier technical direction when the risk assessment changes (see ADR-001).
- Designing a content pipeline around original-content provenance (source and license tracking) rather than bolting on compliance after the fact.
- Structuring governance data (topic registry, source registry, visual-asset registry) as first-class artifacts.
- Writing AI prompts that are explicit about the limits of what AI should decide (scoring and drafting assist only — never final fact-checking or licensing approval).
- Documenting a strategic pivot clearly enough to be auditable by a third party (an ADR, not just an updated README).

## Non-goals (current stage and beyond)

- This system does not replace legal counsel or provide legal advice (see the root [README.md](../README.md) disclaimer).
- This system does not automatically fact-check claims — sources are documented and cited, but factual accuracy review stays a human responsibility.
- This system does not publish content on the user's behalf without a human review checkpoint.
- This system does not aim for mass production — the MVP target is 3 long-form videos and 9-12 Shorts (see [`05-mvp-testing-plan.md`](05-mvp-testing-plan.md)).
