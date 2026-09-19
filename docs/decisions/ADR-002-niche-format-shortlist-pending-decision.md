# ADR-002: Niche & Format Shortlist (Pending Decision)

- **Status: Proposed — pending human decision.** This ADR does not finalize a niche. It presents a provisional shortlist and a non-binding recommendation for a human to review and decide on.
- **Date:** 2026-09-18. **Updated:** 2026-09-19 (audit-driven evidence deepening), then **corrected 2026-09-20** after an independent review found that 3 of the 2026-09-19 pass's "reproducible competition sample" citations pointed to real webpages that did not actually discuss the claimed channels (one — the Economics citation — pointed to a Wikipedia article about an unrelated YouTuber with no connection to economics/finance at all). All 4 competition-sample citations were re-verified; the 3 invalid ones were replaced with real, independently-fetched sources, and one Spanish-language-demand scoring asymmetry between Geography and Economics was corrected. **These corrections changed shortlist membership: Nature & wildlife facts no longer qualifies for the top 4; Infrastructure, engineering & megaprojects now does**, purely as a mechanical consequence of correcting invalid evidence — no niche was manually promoted or demoted.
- **Context:** [`../08-market-research-report.md`](../08-market-research-report.md), [`../09-niche-scoring-methodology.md`](../09-niche-scoring-methodology.md), [`../10-niche-selection-process-map.md`](../10-niche-selection-process-map.md)

## Context

Before committing further resources to European geography as the channel's definitive focus, Stage 2B researched 8 candidate faceless-YouTube niche families using real public sources, scored them on 10 criteria (demand, monetization feasibility, production cost, automation capability, visual-rights availability, long-form/Shorts fit, competition, 12-month sustainability, Europe/international fit, and originality feasibility), and ranked them. Full per-criterion evidence: [`../../templates/niche-scoring-matrix.csv`](../../templates/niche-scoring-matrix.csv). Pivoted comparison: [`../../templates/niche-format-comparison.csv`](../../templates/niche-format-comparison.csv).

## What was wrong, and what changed (2026-09-20 correction)

An independent review of the 2026-09-19 pass verified each of its 4 "reproducible competition sample" source citations by direct fetch. Three did not support their claims at all:

| Niche | Invalid citation | What it actually was | Corrected citation | Old (invalid) count → new (verified) count |
|---|---|---|---|---|
| Geography | `en.wikipedia.org/wiki/Geography_Now` | An article about that one channel only — lists no others | EarthGuessr blog listicle | 7 (fabricated) → 9 (verified) |
| Cities | `en.wikipedia.org/wiki/Not_Just_Bikes` | An article about that one channel only — lists no others | URBANEXUS "Urbanism on YouTube" | 4 (fabricated) → 5 (verified) |
| Economics | `en.wikipedia.org/wiki/Sabrina_Cruz` | A Canadian YouTuber's biography — **no connection to economics/finance at all** | MiniTool listicle | 10 (fabricated) → 7 (verified) |
| Nature/wildlife | `tubics.com/rankings/industries/wildlife-documentaries` | Returned a server error on re-fetch — unconfirmable | Feedspot "90 Wildlife YouTubers" | 11 (unconfirmable) → 15+ confirmed of a claimed 90 |

The corrected sources are genuinely different pages with genuinely different (and honestly reported) channel lists — they were not selected to reproduce the old counts. A separate asymmetry was also fixed: real Spanish-language demand evidence (a comparable channel) was collected for both Geography (Memorias de Pez) and Economics (VisualPolitik) in the 2026-09-19 pass, but only applied to Economics' score. Geography's score now receives the identical treatment.

Full row-level detail with old→new values and sources: [`../../templates/niche-scoring-matrix.csv`](../../templates/niche-scoring-matrix.csv) (rows NLOG-0007, NLOG-0009, NLOG-0027, NLOG-0057, NLOG-0077).

## Provisional shortlist (top 4 by computed total_score, corrected 2026-09-20)

| Rank | Niche | Total score (equal weights) | Total score (revenue-oriented weights) |
|---|---|---|---|
| 1 | European geography, borders & curiosities | 7.5 | 7.38 |
| 2 | Everyday economics & curious data | 7.4 | 7.36 |
| 3 | Cities, transport & urbanism | 7.2 | 6.94 |
| 4 | Infrastructure, engineering & megaprojects | 6.8 | 6.68 |

**Nature & wildlife facts (6.6) is no longer in the top 4** — see its own section below for why, and note that this is a correction of invalid evidence, not new evidence against the niche itself. The remaining non-shortlisted candidates (History 6.3, Science & technology 6.2, Kids/family 5.8) were unaffected by this correction — see the full report for their profiles.

**On the two ranking scenarios:** the top 3 candidates are identical, in nearly the same order, under both equal weights and revenue-oriented weights (Geography and Economics are separated by only 0.02 points under revenue weighting — effectively tied). This robustness across two very different weighting philosophies is itself a meaningful signal.

### 1. European geography, borders & curiosities

**Advantages:** Highest computed score in both weighting scenarios; strong demonstrated demand (RealLifeLore confirmed at 7.94M subscribers, Sept 2026); strong visual-rights availability already proven in this project's own Stage 2 work; a genuine Europe-first, Spanish-language differentiation gap, now backed on equal footing with Economics by real evidence of adjacent Spanish-language demand (Memorias de Pez, ~2.7M subscribers); near-inexhaustible topic supply.

**Disadvantages:** The broad-topic space is genuinely crowded — a corrected, verified competition sample found 9 distinct active incumbent channels (RealLifeLore, Atlas Pro, Wendover Productions, Geography Now, Map Men, Half as Interesting, CGP Grey, GeoWizard, Rainbolt) — requiring ongoing custom map/data-visualization production, a real skill/tool investment.

**Risks:** Standing out against RealLifeLore-scale channels on broad topics; must keep differentiating via the Europe-specific/Spanish-language angle rather than competing head-on globally.

### 2. Everyday economics & curious data

**Advantages:** Highest monetization-feasibility score of all 8 niches; strong, already-proven synergy with this project's Stage 2 research (Eurostat data is real, open, and already used); **the strongest real Spanish-language demand signal found across this entire research effort** — VisualPolitik, confirmed at approximately 3.47 million subscribers, directly adjacent to this niche; a corrected, verified competition sample found this to be the *least* crowded of the top-3 niches by named-incumbent count (7, vs. Geography's 9) — the opposite of what the invalid 2026-09-19 citation claimed.

**Disadvantages:** Requires careful, source-disciplined scripting given the real-money stakes of financial content.

**Risks:** Financial/economic content carries elevated scrutiny (accuracy expectations, potential regulatory sensitivity around anything resembling financial advice) beyond typical geography/urbanism content.

### 3. Cities, transport & urbanism

**Advantages:** Real open-data portals confirmed for 4 European cities (Amsterdam, Barcelona, Berlin, Paris), resolving the original "not verified per-city" gap; a corrected, verified competition sample (URBANEXUS: CityNerd, Banks Rail, Nandert, City Beautiful, Climate Town) found only 5 active incumbent channels — the fewest of any of the top-4 niches; highest Europe/international fit score of all 8 niches (Not Just Bikes is already built around Amsterdam).

**Disadvantages:** Lower raw demand signal than geography or economics in this research pass; the most-cited example (Not Just Bikes) is confirmed personally-narrated, not faceless — a faceless approach in this niche remains less proven; no large Spanish-language comparable was found (only a small ~20K-subscriber channel and one unclear-size channel, Urbanópolis).

**Risks:** Urban-planning content can be perceived as more opinionated/advocacy-adjacent than pure geography or economics facts, which may affect brand-safety/monetization perception (not independently confirmed either way in this pass).

### 4. Infrastructure, engineering & megaprojects

**Advantages:** Enters the shortlist as a direct consequence of this correction, not new research about it specifically — its score (6.8) was never in question and simply now exceeds the corrected Nature/wildlife score. Real demonstrated demand (The B1M: 4M subscribers, 32M viewers/month); real visual-rights baseline already confirmed in this project's Stage 2 work (Gotthard Base Tunnel, 209 CC-licensed Wikimedia Commons files); strong Europe fit (several flagship megaprojects are European).

**Disadvantages:** This niche was **not** part of the 2026-09-19/2026-09-20 deepening passes — its evidence base is one research pass earlier than the other 3 shortlisted niches (no reproducible competition sample, no direct-verification pass on its demand/visual-rights claims). Higher production complexity than the other 3 (technical 3D renders/diagrams).

**Risks:** Because this niche hasn't received the same depth of re-verification as the other 3 shortlisted candidates, a human reviewer should treat it as provisionally shortlisted pending the same level of scrutiny already applied to the others, not as equally vetted.

### Formerly shortlisted: Nature & wildlife facts — now excluded (6.6, rank 5)

This niche was in the top 4 after the original pass (7.3) and remained in the 2026-09-19 pass (6.8, tied with Infrastructure) despite most of its supporting evidence already being flagged as weak. The 2026-09-20 correction re-verified its competition-sample citation: the source cited (tubics.com) could not be reached at all on re-fetch. A genuinely independent replacement source (Feedspot's "90 Wildlife YouTubers" listicle) was found and **corroborates, rather than overturns, the underlying concern**: Brave Wilderness and Epic Wildlife both appear within just the first 15 entries of a page whose title claims 90 total wildlife channels — this is, if anything, stronger evidence that the niche is heavily saturated than the original (invalid) citation provided. Combined with 4 of its 10 scores tracing back to a single commercial blog (OutlierKit, which turned out to run a niche-research tool business — a disclosed conflict of interest) with no independent corroboration ever found for those specific claims, this niche's total_score corrects down to 6.6, below Infrastructure's unchanged 6.8.

**This does not mean Nature & wildlife facts is a bad niche** — its real, confirmed strengths (evergreen broad-appeal demand, a genuine faceless format proven viable via Natural World Facts, real free/public-domain visual pathways via USFWS/Pexels/Pixabay/Unsplash) still stand. It means the original pitch for this niche ("low-cost, low-competition") was built on a source that could not be verified or corroborated, and every version of that specific claim examined so far (across two independent sources now) points the other way.

## Recommendation (non-binding)

Based on the corrected scores and evidence gathered, **European geography, borders & curiosities remains the strongest-scoring candidate in both the equal-weight and revenue-oriented scenarios**, and it earned that position on the same footing as the other 7 niches — its advantages are compounding: proven demand, proven visual-rights availability, and a real, evidenced differentiation gap (Europe-first, Spanish-language, now backed by the same standard of evidence as its closest competitor) rather than a purely re-hashed global-English concept.

**Everyday economics & curious data is now the clear secondary candidate under both weighting scenarios** — a change from the prior version of this ADR, where the secondary candidate depended on which weighting was used. With the corrected evidence, Economics ranks 2nd under equal weights (7.4) and is effectively tied with Geography for 1st under revenue-oriented weights (7.36 vs 7.38). Its case is strengthened, not weakened, by this correction: its competition sample turned out to be *less* crowded than first claimed, not more.

**Infrastructure's presence in the shortlist is a mechanical byproduct of this correction, not a considered recommendation** — a human reviewer should treat it as provisionally shortlisted pending the same depth of re-verification already applied to the other 3.

**This is a recommendation, not a decision.** The final choice, including whether to combine niches, narrow further, request deeper due diligence on Infrastructure before treating it as a true peer to the other 3, or select a candidate not in this shortlist (including reconsidering Nature & wildlife facts if better evidence emerges), is left to human judgment.

## What was NOT decided here

- No niche has been marked as final anywhere in this repository.
- No script, narration, production, or publishing work has begun.
- This ADR's status remains `Proposed` until a human updates it with an actual decision.
