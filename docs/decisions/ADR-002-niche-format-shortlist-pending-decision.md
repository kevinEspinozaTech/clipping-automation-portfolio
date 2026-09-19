# ADR-002: Niche & Format Shortlist (Pending Decision)

- **Status: Proposed — pending human decision.** This ADR does not finalize a niche. It presents a provisional shortlist and a non-binding recommendation for a human to review and decide on.
- **Date:** 2026-09-18. **Updated:** 2026-09-19 (audit-driven evidence deepening). **Corrected 2026-09-20 (source-verification fix):** 3 of the 2026-09-19 pass's "reproducible competition sample" citations were found to point to real webpages that did not actually discuss the claimed channels; these were re-verified and replaced. **Updated again 2026-09-20 (Infrastructure parity pass):** a review of the source-verification fix found that Infrastructure, engineering & megaprojects had entered the shortlist purely because it had never been re-researched to the same depth as the other 3 shortlisted niches — an unfair, non-homogeneous comparison. Infrastructure was then brought through the identical research protocol (reproducible competition sample from a real editorial listicle, direct-verification attempts, Spanish-language demand check, faceless-format audit). **Result: Infrastructure's score dropped from 6.8 to 6.6, and it no longer clearly holds a shortlist place — Nature & wildlife facts (also 6.6) retains the 4th slot via an explicit, disclosed tie-break rule (see below).**
- **Context:** [`../08-market-research-report.md`](../08-market-research-report.md), [`../09-niche-scoring-methodology.md`](../09-niche-scoring-methodology.md), [`../10-niche-selection-process-map.md`](../10-niche-selection-process-map.md)

## Context

Before committing further resources to European geography as the channel's definitive focus, Stage 2B researched 8 candidate faceless-YouTube niche families using real public sources, scored them on 10 criteria (demand, monetization feasibility, production cost, automation capability, visual-rights availability, long-form/Shorts fit, competition, 12-month sustainability, Europe/international fit, and originality feasibility), and ranked them. Full per-criterion evidence: [`../../templates/niche-scoring-matrix.csv`](../../templates/niche-scoring-matrix.csv). Pivoted comparison: [`../../templates/niche-format-comparison.csv`](../../templates/niche-format-comparison.csv).

## What was wrong, and what changed

**2026-09-20, source-verification fix:** an independent review verified each of the 2026-09-19 pass's 4 "reproducible competition sample" source citations by direct fetch. Three did not support their claims at all (e.g., the Economics citation pointed to a Wikipedia biography of an unrelated YouTuber with no connection to economics/finance). All 4 were re-verified against genuinely different real sources; one Spanish-language-demand scoring asymmetry between Geography and Economics was also fixed. Full detail: rows NLOG-0007, NLOG-0009, NLOG-0027, NLOG-0057, NLOG-0077 in the matrix.

**2026-09-20, Infrastructure parity pass:** a follow-up review pointed out that fixing the above had a side effect — Infrastructure entered the shortlist not because it earned it, but because it was the only one of the (then) 5 near-the-cutoff niches that had never been re-researched. Comparing a twice-re-verified Geography/Economics/Cities against an untouched, single-pass Infrastructure was not a fair evaluation. Infrastructure was brought through the identical protocol:

| Criterion | Old value | New value | What changed |
|---|---|---|---|
| `competition_entry_difficulty_score` | 5 (2-3 named channels, no real sample) | 4 | Real editorial listicle (WorthWatch, directly fetched and confirmed) names 12-16 channels — the most crowded of the 4, not among the least |
| `visual_legal_availability_score` | 7 (one example, Gotthard) | 8 | A second real megaproject (Golden Gate Bridge) independently confirmed strong Wikimedia Commons coverage, corroborating the pattern rather than resting on one example |
| `originality_feasibility_score` | 8 (assumed) | 6 | Faceless-format audit found no unambiguous genuinely-faceless big channel in this niche — The B1M is confirmed host-led; Ultimate Mega Projects' "digital host" format is ambiguous |
| All other criteria | — | unchanged | Re-checked; no better public evidence existed to justify a change either way |

**Net effect: total_score 6.8 → 6.6.** Full detail: rows NLOG-0011 through NLOG-0020 in the matrix.

## Provisional shortlist (top 4 by computed total_score, updated 2026-09-20)

| Rank | Niche | Total score (equal weights) | Total score (revenue-oriented weights) |
|---|---|---|---|
| 1 | European geography, borders & curiosities | 7.5 | 7.38 |
| 2 | Everyday economics & curious data | 7.4 | 7.36 |
| 3 | Cities, transport & urbanism | 7.2 | 6.94 |
| 4 | Nature & wildlife facts | 6.6 | 6.63 |

**Infrastructure, engineering & megaprojects (6.6) is tied with Nature & wildlife facts under equal weights, but loses under revenue-oriented weights (6.52 vs. 6.63).** Per the explicit tie-break rule stated below, Nature & wildlife facts retains the 4th slot because it is never worse than Infrastructure in either weighting scenario, and strictly better in one. This is a mechanical tie-break, not a judgment that Nature & wildlife facts is the better business — see its own risk profile below, which remains serious.

**Tie-break rule (stated before, not after, seeing which niche it favors):** when two niches are tied under equal weights, the revenue-oriented weighting decides — whichever niche is not strictly worse under either scenario, and strictly better under at least one, keeps the shortlist slot.

The remaining non-shortlisted candidates (History 6.3, Science & technology 6.2, Kids/family 5.8) were unaffected by either correction pass.

**On the two ranking scenarios:** the top 3 candidates are identical, in nearly the same order, under both equal weights and revenue-oriented weights (Geography and Economics are separated by only 0.02–0.04 points — effectively tied). This robustness across two very different weighting philosophies is itself a meaningful signal. The 4th slot is genuinely close and scenario-dependent — treat it with correspondingly less confidence than the top 3.

### 1. European geography, borders & curiosities

**Advantages:** Highest computed score in both weighting scenarios; strong demonstrated demand (RealLifeLore, 7.9-9M subscribers per an independent blog source); strong visual-rights availability already proven in this project's own Stage 2 work; a genuine Europe-first, Spanish-language differentiation gap, now backed on equal footing with Economics by real evidence of adjacent Spanish-language demand (Memorias de Pez -- a real channel with two unverified but roughly-agreeing estimates in the low millions, per the 2026-09-21 cleanup note in the report); near-inexhaustible topic supply.

**Disadvantages:** The broad-topic space is genuinely crowded — a corrected, verified competition sample found 9 distinct active incumbent channels — requiring ongoing custom map/data-visualization production, a real skill/tool investment.

**Risks:** Standing out against RealLifeLore-scale channels on broad topics; must keep differentiating via the Europe-specific/Spanish-language angle rather than competing head-on globally.

### 2. Everyday economics & curious data

**Advantages:** Highest monetization-feasibility score of all 8 niches; strong, already-proven synergy with this project's Stage 2 research (Eurostat data is real, open, and already used); **the strongest real Spanish-language demand signal found across this entire research effort** — VisualPolitik, confirmed at approximately 3.47 million subscribers; a verified competition sample found this to be the *least* crowded of the top-3 niches by named-incumbent count (7, vs. Geography's 9).

**Disadvantages:** Requires careful, source-disciplined scripting given the real-money stakes of financial content.

**Risks:** Financial/economic content carries elevated scrutiny (accuracy expectations, potential regulatory sensitivity around anything resembling financial advice) beyond typical geography/urbanism content.

### 3. Cities, transport & urbanism

**Advantages:** Real open-data portals confirmed for 4 European cities (Amsterdam, Barcelona, Berlin, Paris); a verified competition sample (URBANEXUS) found only 5 active incumbent channels — the fewest of any niche evaluated at parity; highest Europe/international fit score of all 8 niches.

**Disadvantages:** Lower raw demand signal than geography or economics; the most-cited example (Not Just Bikes) is confirmed personally-narrated, not faceless; no large Spanish-language comparable was found.

**Risks:** Urban-planning content can be perceived as more opinionated/advocacy-adjacent than pure geography or economics facts, which may affect brand-safety/monetization perception (not independently confirmed either way).

### 4. Nature & wildlife facts (retains shortlist slot via tie-break — treat with reduced confidence)

**Advantages:** Still evergreen, broad-appeal demand (Natural World Facts confirmed at 950K+ subscribers, 110M views); a genuine faceless format is proven viable (Natural World Facts, confirmed not host-led) — unlike Infrastructure, where no unambiguous faceless comparable was found; real, verified pathways to legally-free visual material (US Fish & Wildlife Service public-domain library; Pexels/Pixabay/Unsplash).

**Disadvantages:** This niche's score dropped the most of any candidate researched so far (7.3 → 6.6) after its supporting claims were audited. Four of its ten original scores traced to a single commercial blog (OutlierKit, which turned out to run a niche-research tool business — a disclosed conflict of interest). A verified competition sample found this to be the **most crowded of all 4 niches evaluated at parity** (15+ of a claimed 90 channels) — the opposite of the original "low competition" pitch.

**Risks:** The original business case for this niche ("low-cost, low-competition") is **not substantiated** by any source checked so far — treat it as a genuinely open question, not a settled advantage, if reconsidering this niche.

### Also evaluated at parity, not shortlisted: Infrastructure, engineering & megaprojects (6.6, tied but loses tie-break)

Brought through the identical research protocol as the 3 clearly-shortlisted niches (see table above). **Advantages:** Real, primary-sourced demand (The B1M: 4M subscribers/32M viewers-per-month, official site) plus confirmation that even larger channels exist in this space (Real Engineering 5.1M, Practical Engineering 4.8M); two independently-confirmed real megaprojects (Gotthard, Golden Gate Bridge) with strong Wikimedia Commons coverage. **Disadvantages:** The verified competition sample is the most crowded of any niche evaluated at parity (12-16 named channels vs. 5-9 for the other 3); no unambiguous genuinely-faceless big channel was found (The B1M is host-led; Ultimate Mega Projects' format is ambiguous); a real Spanish-language channel exists (MegaProyectos España) but its audience size could not be verified, unlike Geography's and Economics' Spanish-demand evidence. **This niche was not rejected — it was evaluated fairly and did not clearly outperform its closest competitor.** It remains a reasonable candidate for reconsideration if either its own evidence improves (e.g., a verified Ultimate Mega Projects subscriber count, a confirmed faceless format) or Nature & wildlife facts' risks prove disqualifying on human review.

## Recommendation (non-binding)

**European geography, borders & curiosities remains the strongest-scoring candidate in both weighting scenarios**, on the same footing as the other 7 niches — proven demand, proven visual-rights availability, and a real, evidenced Europe-first/Spanish-language differentiation gap.

**Everyday economics & curious data is the clear secondary candidate under both weighting scenarios**, effectively tied with Geography for 1st under revenue-oriented weights (7.36 vs 7.38).

**The 4th shortlist slot (Nature & wildlife facts vs. Infrastructure, engineering & megaprojects) is genuinely close and should be treated as an open question, not a settled ranking.** Nature & wildlife facts holds the slot only by a disclosed, mechanical tie-break rule, not because its business case is stronger — its "low competition" pitch has been directly contradicted by two independent real sources now. Infrastructure has a cleaner demand and visual-rights story but the most crowded competitive field of any niche evaluated and an unproven faceless format. **A reasonable alternative reading of this same evidence is to treat both as tied 4th-place candidates requiring further human judgment, rather than picking either.**

**This is a recommendation, not a decision.** The final choice, including whether to combine niches, narrow further, request deeper due diligence on either 4th-place candidate, or select a candidate not in this shortlist, is left to human judgment.

## What was NOT decided here

- No niche has been marked as final anywhere in this repository.
- No script, narration, production, or publishing work has begun.
- This ADR's status remains `Proposed` until a human updates it with an actual decision.
