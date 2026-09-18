# 08 — Market Research Report: Faceless YouTube Niches & Formats (Stage 2B)

**Research date:** 2026-09-18. **Scope:** 8 candidate niche families, 16 real comparable channels/videos, scored on 10 criteria. Full evidence trail: [`../templates/channel-video-registry.csv`](../templates/channel-video-registry.csv) (dossiers) and [`../templates/niche-scoring-matrix.csv`](../templates/niche-scoring-matrix.csv) (per-criterion scores + sources). Methodology: [`09-niche-scoring-methodology.md`](09-niche-scoring-methodology.md). This report does not select a final niche — see [`decisions/ADR-002-niche-format-shortlist-pending-decision.md`](decisions/ADR-002-niche-format-shortlist-pending-decision.md) for the provisional shortlist and non-binding recommendation.

## Methodology summary

For each of 8 niche families, 2 real channels/videos were identified via public web search and, where possible, official/primary sources (e.g., a channel's own site, YouTube's own policy pages). Every dossier records only what could actually be observed or reasonably cited — a real subscriber/view count with its source, or `NOT_PUBLICLY_AVAILABLE` where no public figure could be found. No RPM, revenue, retention, or internal competition metric was ever estimated or invented; where such figures appear in secondary sources (e.g., a third-party "estimated earnings" figure), they are noted as unverified context only and excluded from scoring. Each niche was then scored on 10 criteria (0-10, higher = better), with every score's basis — `OBSERVED`, `ESTIMATED`, `INFERRED`, or `EDITORIAL_OPINION` — logged individually.

## Findings by niche family

### 1. European geography, borders & curiosities
Real examples: **RealLifeLore** (7.9-9M subscribers) and **Half as Interesting** (weekly since Aug 2017, 5-12 min videos). Strong, proven demand; the dominant incumbents are globally/US-oriented in English, leaving a real gap for a Europe-first, Spanish-language angle. Visual-legal availability is strong — already demonstrated in this project's own Stage 2 research (Wikimedia Commons categories confirmed for Baarle-Hertog, Vaalserberg, etc.). **Total score: 7.4 (rank 1).**

### 2. Infrastructure, engineering & megaprojects
Real examples: **The B1M** (4M subscribers, 32M viewers/month, official weekly Wednesday upload schedule) and **Ultimate Megaprojects**. Strong demand and good European topic supply (Gotthard Base Tunnel, etc. — already researched in Stage 2), but The B1M itself is host-led (Fred Mills on camera), not purely faceless, and technical 3D-render production raises cost/complexity. **Total score: 6.8 (rank 5).**

### 3. Cities, transport & urbanism
Real examples: **Not Just Bikes** (personal, host-narrated) and **City Beautiful** (top video: 5.7M views, on Gary, Indiana). The best-known example in this niche (Not Just Bikes) is built around a European city (Amsterdam) already — the strongest "Europe fit" score of all 8 niches researched. Somewhat less raw demand than geography or history. **Total score: 7.0 (rank 4).**

### 4. History explained visually
Real examples: **Kings and Generals** (4.07M subscribers, 1,919 videos, Jan 2026) and **The Armchair Historian** (2.49M subscribers). Strong demand and good evergreen supply, but this is the **most saturated** niche researched (multiple well-resourced multi-million-subscriber incumbents), and notably, The Armchair Historian — a successful, well-funded channel — announced an **indefinite hiatus in December 2025**, a real signal that production sustainability is a genuine operator-level risk here, not just a topic-supply question. **Total score: 6.3 (rank 6).**

### 5. Science & technology
Real examples: **Kurzgesagt** (large multi-million subscriber channel) and **Animagraffs** (1.7M subscribers, 146M views). Technology is explicitly cited by industry sources as a top-CPM advertiser category, but this niche has the **lowest competition-entry-difficulty score** of all 8 (i.e., the most saturated by well-funded incumbents) and requires the highest-skill original animation to compete credibly. **Total score: 6.2 (rank 7).**

### 6. Everyday economics & curious data
Real examples: **Economics Explained** (2.85M subscribers, 359.3M total views) and **Two Cents** (2.1M subscribers, PBS Digital Studios, host-led). Finance is explicitly cited as the single highest-CPM faceless category by industry sources. Strong synergy with this project's own Stage 2 research: Eurostat data (already used for a real topic) is openly licensed and directly reusable for this niche. **Total score: 7.1 (rank 3).**

### 7. Kids/family education (Made for Kids)
Real examples: **Homeschool Pop** and **FreeSchool** (both host-narrated, not faceless; subscriber counts not publicly found in this pass). This niche's monetization is **structurally and officially restricted**: YouTube's own "Made for Kids" policy (verified directly against `support.google.com`) disables personalized ads, comments, Super Chat/Stickers/Thanks, Channel Memberships, end screens, and cards; industry sources report resulting RPM around $1-3 versus $5-15 for general content (an estimate, not an official YouTube figure). Combined with COPPA and the EU's GDPR-K compliance burden, this niche's `originality_feasibility` criterion was left `REQUIRES_MANUAL_REVIEW` pending dedicated legal review. **Total score: 5.8 (rank 8, lowest).**

### 8. Nature & wildlife facts (evidence-selected 8th candidate)
Selected after a broad search for "current faceless niche opportunity" surfaced this category repeatedly (OutlierKit and similar industry sources) as low-competition and low-cost specifically because of abundant available stock footage. Real examples: **Natural World Facts** (active since 2012, "Deep Sea Wonders" series) and **Brave Wilderness/Coyote Peterson** (1.19M subscribers this channel, 22.99M combined; explicitly host-led, not faceless). Important honest caveat surfaced during research: the niche's low cost is partly explained by reliance on **licensed/stock wildlife footage** rather than self-produced material — a genuinely faceless, originally-sourced approach here needs the same per-asset visual-rights discipline as any other niche, not an automatic pass. **Total score: 7.3 (rank 2).**

## Cross-cutting observations

- **Format pattern:** among the 16 real channels researched, several of the most successful in "softer"/lifestyle-adjacent niches (The B1M, Not Just Bikes, Two Cents, Homeschool Pop, Brave Wilderness) actually use an on-camera host or personal narrator, not a purely faceless format — while the more data/fact-driven niches (geography, history, science, economics) skew more purely faceless. This is a real, observed pattern relevant to production planning, not an assumption.
- **Language gap:** every real comparable example found across all 8 niches is English-language. No directly comparable large Spanish-language faceless channel was identified in this research pass for any niche — this is itself a data point (an apparent gap/opportunity) but should be treated as `REQUIRES_MANUAL_REVIEW` rather than proof of low competition, since Spanish-language search wasn't exhaustively covered here.
- **Monetization ceiling for kids' content is real and officially documented**, not assumed — directly confirmed against YouTube's own policy pages.
- **No RPM, revenue, retention, or internal competition metric is presented anywhere in this report or its underlying CSVs as a hard number** — every such figure is either absent (`NOT_PUBLICLY_AVAILABLE`) or explicitly labeled as a third-party estimate.

## Limitations

- 2 real examples per niche is a bounded sample, not an exhaustive market survey — useful for relative comparison, not a substitute for deeper due diligence on any single finalist.
- Several dossier fields (exact publish cadence, typical duration, subscriber counts for smaller channels) came back `NOT_PUBLICLY_AVAILABLE` or `REQUIRES_MANUAL_REVIEW` in this pass — see [`../templates/channel-video-registry.csv`](../templates/channel-video-registry.csv) for exactly which.
- Scoring relies heavily on `EDITORIAL_OPINION`/`INFERRED` judgment for several criteria (production cost, automation capability) since no public source quantifies these directly — this is disclosed, not hidden, per [`09-niche-scoring-methodology.md`](09-niche-scoring-methodology.md).
- This report does not constitute legal advice, particularly regarding the Kids/family niche's COPPA/GDPR-K obligations — see the disclaimer in the root [README.md](../README.md).
