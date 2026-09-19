# 09 — Niche & Format Scoring Methodology (Stage 2B)

This document defines how the 8 candidate niches/formats in [`../templates/niche-format-comparison.csv`](../templates/niche-format-comparison.csv) are scored, how the total is computed, and how every number traces back to [`../templates/niche-scoring-matrix.csv`](../templates/niche-scoring-matrix.csv). It follows the same reproducibility principle established in [`07-topic-scoring-methodology.md`](07-topic-scoring-methodology.md), extended with an explicit **data-type classification** for every value.

## Data-type classification

Every row in `niche-scoring-matrix.csv` carries a `data_type`:

| Value | Meaning |
|---|---|
| `OBSERVED` | Directly stated by a real, cited source (a subscriber count, a view count, an official policy statement). |
| `ESTIMATED` | A disclosed, methodical approximation derived from observed data. |
| `INFERRED` | A reasoned conclusion drawn from observed evidence (e.g., "highly saturated" inferred from several multi-million-subscriber incumbents). |
| `EDITORIAL_OPINION` | A transparent, subjective judgment call — labeled as such, never disguised as measured fact. |
| `NOT_PUBLICLY_AVAILABLE` | The underlying fact (RPM, exact revenue, YouTube-internal competition/retention data) is not publicly obtainable. |
| `REQUIRES_MANUAL_REVIEW` | Needs a human to investigate further (e.g., legal review) before it can be scored with confidence. |

**No score is ever presented as more certain than its data type.** `EDITORIAL_OPINION` and `INFERRED` are legitimate, expected inputs — most of the 10 criteria below are not things any public source states as a number, and pretending otherwise would itself be a form of fabrication. What must never happen is presenting a guess as `OBSERVED`, or inventing RPM/revenue/retention/competition figures that don't exist publicly — those stay `NOT_PUBLICLY_AVAILABLE`.

## The ten criteria

Each of the user's ten evaluation objectives becomes one scored dimension, 0-10, **higher = more favorable**:

| # | Criterion | `criterion` value in the matrix | Direction note |
|---|---|---|---|
| 1 | Demand & viral potential | `demand_viral_score` | Higher = more demand. |
| 2 | Real monetization possibility | `monetization_feasibility_score` | Scored as a **feasibility judgment** (ad-category tier, policy restrictions), never as an invented RPM or revenue figure — those stay `NOT_PUBLICLY_AVAILABLE` wherever cited. |
| 3 | Production ease & cost | `production_ease_cost_score` | Higher = easier/cheaper. |
| 4 | Automation capability | `automation_capability_score` | Higher = more automatable with this project's current tooling. |
| 5 | Legal availability of visual material | `visual_legal_availability_score` | Higher = more legally available material (confirmed via real sourcing, e.g. the Wikimedia Commons checks reused from Stage 2). |
| 6 | Potential for long-form and Shorts | `long_and_shorts_potential_score` | Higher = works well in both formats. |
| 7 | Competition & entry difficulty | `competition_entry_difficulty_score` | Higher = **easier** to enter / less saturated (same convention as Stage 2's `competition_score`). |
| 8 | 12-month sustainability | `sustainability_12mo_score` | Higher = more topic/content supply for at least a year. |
| 9 | Fit for a European/international audience | `europe_international_fit_score` | Higher = better fit. |
| 10 | Feasibility of original (non-reused, non-mass-generated) content | `originality_feasibility_score` | Higher = easier to do originally and differentiated. |

## Computing `total_score`

1. Take every criterion with a real numeric value (`OBSERVED`, `ESTIMATED`, `INFERRED`, or `EDITORIAL_OPINION` all count — `NOT_PUBLICLY_AVAILABLE` and `REQUIRES_MANUAL_REVIEW` do not).
2. **If fewer than 6 of the 10 criteria have a real numeric value, `total_score` must be `REQUIRES_MANUAL_REVIEW`, not a number.**
3. Otherwise, `total_score` is the equal-weighted mean (default weight `1/10` per criterion, adjustable in future passes) of the measured criteria.

This mirrors Stage 2's reproducibility rule: `total_score` = sum(weight × value) over measured rows for that `niche_id`, divided by the sum of those weights — recomputed and verified against every value in `niche-scoring-matrix.csv` before this stage's PR was opened.

## Ranking and shortlisting

`rank` orders niches by `total_score` (numeric totals only). `shortlisted = TRUE` is set for the top-ranked candidates chosen for [`../docs/decisions/ADR-002-niche-format-shortlist-pending-decision.md`](decisions/ADR-002-niche-format-shortlist-pending-decision.md) — **this ranking is an input to a human decision, not the decision itself.** A numeric edge of a few tenths of a point between adjacent niches should not be read as a definitive verdict given how many criteria rest on `EDITORIAL_OPINION`/`INFERRED` judgment rather than hard measurement.

## Alternate weighting: revenue-oriented scenario

The default equal weighting (1/10 per criterion) is not the only lens worth applying. A **revenue-oriented weighting**, provided here as a second, informational ranking (never a replacement for the default), emphasizes criteria most tied to near-term monetization:

| Criterion | Revenue-oriented weight |
|---|---|
| Demand & viral potential | 15% |
| Monetization feasibility | 15% |
| Production ease & cost | 12% |
| Automation capability | 10% |
| Visual-legal availability | 12% |
| Long-form/Shorts potential | 7% |
| Competition & entry difficulty | 8% |
| 12-month sustainability | 8% |
| Europe/international fit | 3% |
| Originality feasibility | 10% |

Computed the same way as the default (renormalized over whichever criteria have a real numeric value), this weighting is tracked **alongside**, not instead of, the equal-weighted `total_score` in [`../templates/niche-format-comparison.csv`](../templates/niche-format-comparison.csv) notes and in [`08-market-research-report.md`](08-market-research-report.md). As of the 2026-09-20 correction, both scenarios keep the same top 4 niches (geography, economics, cities/urbanism, infrastructure), with geography and economics effectively tied for 1st under revenue-oriented weights.

## Revising scores: only when new evidence justifies it

A score is revised only when genuinely new evidence changes the picture — never merely to make a preferred candidate look better. Every revision must show the prior value, the new value, and the specific evidence that justified the change, logged directly in the `notes` field of the affected row in `niche-scoring-matrix.csv`. The 2026-09-19 deepening pass (see [`08-market-research-report.md`](08-market-research-report.md) addendum) is a worked example: 9 of the 40 scored rows across the 4 shortlisted niches were revised, each with an explicit "REVISED from X to Y" note citing the new source; the other 31 rows were left untouched because the new research did not contradict or add to them.

**A citation is only as good as its verification.** The 2026-09-20 correction (see the report addendum and [`decisions/ADR-002-niche-format-shortlist-pending-decision.md`](decisions/ADR-002-niche-format-shortlist-pending-decision.md)) found that 3 of the 2026-09-19 pass's "reproducible sample" citations pointed to real, live URLs that nonetheless did not support the claim attached to them — a mismatch that a plausibility check alone would not catch, since the URLs were real and topically adjacent. The lesson applied going forward: a citation is not verified until its actual content has been read and confirmed to state what the note claims it states, not merely confirmed to exist or resolve.

## Why monetization is scored as feasibility, not revenue

YouTube does not publish per-channel RPM, ad revenue, or retention data, and no legitimate public source provides it either — any number claiming to be a channel's "earnings" found during research is a third-party estimate, not a disclosed fact. This project therefore never scores `monetization_feasibility_score` from a specific dollar figure. Instead it scores structural feasibility: whether the niche falls in a historically ad-friendly category, whether platform policy (e.g., YouTube's Made for Kids rules) disables monetization features, and similar publicly documented, non-financial signals. Where a third-party revenue *estimate* is mentioned in a dossier for context, it is explicitly labeled as an unverified estimate and excluded from the scored value.
