# 01 — Business Case

## Problem

Creators, brands, and media teams increasingly rely on short-form vertical video to drive discovery and audience growth. Manually producing clips from long-form source video is slow and does not scale, but most "auto-clipping" tools in the market optimize purely for speed and ignore content-rights risk — treating public availability or platform features (like a native "Clip" button) as if they were legal permission to reuse and monetize content. This creates real exposure: copyright claims, platform strikes, revenue clawbacks, and reputational harm.

## Opportunity

A pipeline that combines automation (for speed and consistency) with a **non-negotiable rights-verification gate** (for safety) can capture the scaling benefits of automated clipping without inheriting its most common risk. This is also a strong portfolio demonstration: it shows the ability to design systems that are not just technically functional, but operationally and legally responsible.

## Target outcome

A repeatable process where:

- Every source video has a documented, human-reviewed rights status before any processing occurs.
- Only explicitly authorized content reaches transcription, AI analysis, clip generation, and publishing.
- Every clip that goes out carries a traceable link back to its source's verified rights record.
- Performance data feeds back into which sources and segment types are worth revisiting.

## Why this belongs in a portfolio

This project demonstrates:

- Designing a workflow automation system (n8n) around a hard compliance gate rather than bolting compliance on afterward.
- Structuring governance data (rights registry, content registry) as first-class artifacts, not an afterthought.
- Writing AI prompts that are explicit about the limits of what AI should decide.
- Documenting a system clearly enough that its safeguards are auditable by a third party.

## Non-goals (Stage 1 and beyond)

- This system does not replace legal counsel or provide legal advice (see the root [README.md](../README.md) disclaimer).
- This system does not attempt to automatically interpret "fair use" or infer authorization from public availability.
- This system does not publish content on the user's behalf without a human review checkpoint.
