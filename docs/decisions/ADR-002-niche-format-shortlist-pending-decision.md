# ADR-002: Niche & Format Shortlist (Pending Decision)

- **Status: Proposed — pending human decision.** This ADR does not finalize a niche. It presents a provisional shortlist and a non-binding recommendation for a human to review and decide on.
- **Date:** 2026-09-18. **Updated:** 2026-09-19, following an audit-driven deepening of the evidence for all 4 shortlisted niches (see the addendum in [`../08-market-research-report.md`](../08-market-research-report.md)). Shortlist membership was **not** changed by the update — only scores, internal ranking, and the risk/advantage detail below.
- **Context:** [`../08-market-research-report.md`](../08-market-research-report.md), [`../09-niche-scoring-methodology.md`](../09-niche-scoring-methodology.md), [`../10-niche-selection-process-map.md`](../10-niche-selection-process-map.md)

## Context

Before committing further resources to European geography as the channel's definitive focus, Stage 2B researched 8 candidate faceless-YouTube niche families using real public sources, scored them on 10 criteria (demand, monetization feasibility, production cost, automation capability, visual-rights availability, long-form/Shorts fit, competition, 12-month sustainability, Europe/international fit, and originality feasibility), and ranked them. Full per-criterion evidence: [`../../templates/niche-scoring-matrix.csv`](../../templates/niche-scoring-matrix.csv). Pivoted comparison: [`../../templates/niche-format-comparison.csv`](../../templates/niche-format-comparison.csv).

## Provisional shortlist (top 4 by computed total_score, updated 2026-09-19)

| Rank | Niche | Total score (equal weights) | Total score (revenue-oriented weights) |
|---|---|---|---|
| 1 | European geography, borders & curiosities | 7.3 (was 7.4) | 7.27 |
| 2 | Cities, transport & urbanism | 7.2 (was 7.0, up 2 ranks) | 6.94 |
| 3 | Everyday economics & curious data | 7.1 (unchanged) | 7.12 |
| 4 | Nature & wildlife facts | 6.8 (was 7.3, down 2 ranks) | 6.79 |

**Important, explicitly flagged tie:** Nature & wildlife facts (6.8) now exactly ties **Infrastructure, engineering & megaprojects** (6.8, not shortlisted) under equal weights, after nature/wildlife's scores were revised down. This ADR does not resolve that tie or change shortlist membership — it is flagged here for human attention. The next four candidates (Infrastructure 6.8, History 6.3, Science & technology 6.2, Kids/family 5.8) were researched with the same rigor but did not make the shortlist — see the full report for their profiles.

### 1. European geography, borders & curiosities

**Advantages:** Highest computed score in both weighting scenarios; strong demonstrated demand (RealLifeLore confirmed at 7.94M subscribers, Sept 2026); strong visual-rights availability already proven in this project's own Stage 2 work; a genuine Europe-first, Spanish-language differentiation gap — strengthened, not just assumed, by newly confirmed evidence that adjacent Spanish-language content (Memorias de Pez, ~2.7M subscribers) draws a large real audience; near-inexhaustible topic supply.

**Disadvantages:** The broad-topic space is more crowded than first scored — a reproducible sample found 7 distinct active incumbent channels, not just 2 — requiring ongoing custom map/data-visualization production, a real skill/tool investment.

**Risks:** Standing out against RealLifeLore-scale channels on broad topics; must keep differentiating via the Europe-specific/Spanish-language angle rather than competing head-on globally.

### 2. Cities, transport & urbanism

**Advantages:** Moved up 2 ranks after this pass: real open-data portals confirmed for 4 European cities (Amsterdam, Barcelona, Berlin, Paris), resolving the prior "not verified" gap; a reproducible competition sample found only 4 active incumbent channels — the fewest of any of the 4 shortlisted niches, i.e. genuinely the least saturated; highest Europe/international fit score of all 8 niches (Not Just Bikes is already built around Amsterdam).

**Disadvantages:** Lower raw demand signal than geography in this research pass; the most-cited example (Not Just Bikes) is confirmed personally-narrated, not faceless — a faceless approach in this niche remains less proven than for geography; no large Spanish-language comparable was found (only a small ~20K-subscriber channel and one unclear-size channel, Urbanópolis).

**Risks:** Urban-planning content can be perceived as more opinionated/advocacy-adjacent than pure geography facts, which may affect brand-safety/monetization perception (not independently confirmed either way in this pass).

### 3. Everyday economics & curious data

**Advantages:** Highest monetization-feasibility score of all 8 niches; strong, already-proven synergy with this project's Stage 2 research (Eurostat data is real, open, and already used); **the strongest real Spanish-language demand signal found across this entire research effort** — VisualPolitik, confirmed at approximately 3.47 million subscribers, directly adjacent to this niche.

**Disadvantages:** Confirmed the **most crowded** of the 4 shortlisted niches by the reproducible competition sample (10 distinct active channels found) — more saturated than the original pass suggested; requires careful, source-disciplined scripting given the real-money stakes of financial content.

**Risks:** Financial/economic content carries elevated scrutiny (accuracy expectations, potential regulatory sensitivity around anything resembling financial advice) beyond typical geography/urbanism content.

### 4. Nature & wildlife facts

**Advantages:** Still evergreen, broad-appeal demand (Natural World Facts confirmed at 950K+ subscribers, 110M views); genuine faceless format proven viable (Natural World Facts, confirmed not host-led) alongside a confirmed host-led alternative (Brave Wilderness) in the same niche; real, verified pathways to legally-free visual material now identified (US Fish & Wildlife Service public-domain library; Pexels/Pixabay/Unsplash free-commercial-use license terms).

**Disadvantages:** **This niche's score dropped the most of any candidate in this pass (7.3 → 6.8) after its supporting claims were audited.** Four of its ten scores traced to a single commercial blog (OutlierKit, which turned out to run a niche-research tool business — a disclosed conflict of interest) with no independent corroboration found; a reproducible competition sample found **11 distinct active channels — the most of any of the 4 shortlisted niches**, directly contradicting the original "low competition" premise. Legally-free visual material is real but more limited than first claimed — premium/rare-species footage still commonly requires a paid license.

**Risks:** The business case for this niche was weaker than it first appeared, once its evidence was audited — any human decision to proceed here should treat the original "low-cost, low-competition" framing as **not substantiated** and re-evaluate from the revised evidence in [`../08-market-research-report.md`](../08-market-research-report.md) and [`../../templates/niche-scoring-matrix.csv`](../../templates/niche-scoring-matrix.csv) rather than the original pitch. Weakest natural fit with a "European geography" brand identity if that identity is kept.

## Recommendation (non-binding)

Based on the computed scores and the evidence gathered (including the 2026-09-19 deepening pass), **European geography, borders & curiosities remains the strongest-scoring candidate in both the equal-weight and revenue-oriented scenarios**, and it earned that position on the same footing as the other 7 niches, not by assumption — its advantages are compounding: proven demand, proven visual-rights availability, and a real, evidenced differentiation gap (Europe-first, Spanish-language, now further supported by real adjacent-content audience data) rather than a purely re-hashed global-English concept.

The secondary candidate differs by weighting scenario, which is itself a useful signal for human judgment: under **equal weights**, **Cities, transport & urbanism** is now the strongest secondary candidate (rank 2, up from rank 4), driven by confirmed lower competition and resolved visual-legal availability. Under the **revenue-oriented weighting**, **Everyday economics & curious data** remains the stronger secondary candidate, given its superior monetization profile and the newly confirmed, very large Spanish-language audience adjacent to it (VisualPolitik). **Nature & wildlife facts**, the prior second-place candidate, should be treated with markedly reduced confidence following this pass — its business case rested substantially on a single, conflicted, uncorroborated source.

**This is a recommendation, not a decision.** The final choice, including whether to combine niches, narrow further, resolve the geography/infrastructure-adjacent tie noted above, or select a candidate not in this shortlist, is left to human judgment.

## What was NOT decided here

- No niche has been marked as final anywhere in this repository.
- No script, narration, production, or publishing work has begun.
- This ADR's status remains `Proposed` until a human updates it with an actual decision.
