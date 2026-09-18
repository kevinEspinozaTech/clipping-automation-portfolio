# 07 — Topic Scoring Methodology

This document defines how candidate topics in [`../templates/topic-registry.csv`](../templates/topic-registry.csv) are scored, how the score is computed, and the hard blocking rule that overrides the score. It is designed to be **transparent, reproducible, and adjustable** — every number in the registry should be traceable back to a row in [`../templates/topic-scoring-log.csv`](../templates/topic-scoring-log.csv).

## The no-fabrication rule

**A score is never invented to fill a gap.** If a real data point is not available (e.g., no access to live YouTube search-trend or competition data), the corresponding entry is recorded as `NOT_MEASURED`. If a data point requires a judgment call that hasn't been confirmed by a human yet, it is recorded as `REQUIRES_MANUAL_REVIEW`. Both are valid, expected values — not errors.

Every row in `topic-scoring-log.csv` that carries a real value must also carry `source`, `source_url`, and `consulted_at`. Rows without a real external source (e.g., an internal editorial judgment call) must say so explicitly in `notes` rather than imply an external citation that doesn't exist.

## The seven dimensions

All scores are 0-10, and **all use the same direction: higher = more favorable to produce this topic.**

| Dimension | `dimension` value in the log | What it measures |
|---|---|---|
| Demand | `demand_score` | Estimated audience interest / search demand. |
| Competition | `competition_score` | Room to stand out — **higher = less saturated**, not higher = more competitors. |
| Evergreen value | `evergreen_score` | How durable the topic's relevance is (vs. news-cycle-dependent). |
| Source availability | `source_availability_score` | Depth/reliability of factual sources found. |
| Visual rights availability | `visual_rights_availability_score` | How feasible it is to legally source supporting maps/photos/footage. |
| Production ease | `production_ease_score` | **Higher = easier** to produce (inverse of difficulty). |
| Monetization safety | `monetization_safety_score` | How safe the topic is for monetized publishing (no sensitive/controversial content risk). |

`demand_score` and `competition_score` require live search/YouTube trend data this project does not have access to in its current (non-automated, no-paid-API) stage — they are expected to be `NOT_MEASURED` until a human supplies real data (e.g., from YouTube Studio, Google Trends) or a future stage integrates a real (and explicitly approved) data source.

## Default weights

All seven dimensions are weighted equally by default (`1/7` each). This is a starting point, not a fixed rule — adjust the weights in a future scoring pass if, for example, monetization safety or visual-rights availability should matter more than evergreen value for a given content strategy. Any change in weighting must be reflected in the `weight` column of new `topic-scoring-log.csv` rows, not applied retroactively to old ones.

## Computing `final_score`

1. Take every dimension that has a real numeric value (i.e., not `NOT_MEASURED`).
2. **If fewer than 4 of the 7 dimensions have a real numeric value, `final_score` must be `REQUIRES_MANUAL_REVIEW`, not a number.** Too little real data does not get averaged into a false sense of confidence.
3. Otherwise, `final_score` is the weighted average of the measured dimensions only, using their respective weights (equal weights by default → a simple arithmetic mean of whatever was actually measured).

This makes `final_score` fully reproducible from `topic-scoring-log.csv`: sum(weight × value) over measured rows for that `topic_id`, divided by the sum of those weights.

## The blocking rule (hard gate, independent of the score)

Two fields on `topic-registry.csv` act as **hard gates**, independent of `final_score`:

- `sources_available_status`
- `visual_resources_feasible_status`

Each is one of: `NOT_MEASURED`, `REQUIRES_MANUAL_REVIEW`, `CONFIRMED`, `INSUFFICIENT`.

- **If either gate is `INSUFFICIENT`**, the topic is forced to `status = BLOCKED_NO_SOURCES` or `status = BLOCKED_NO_VISUAL_RIGHTS` respectively, and `recommended = FALSE` — **regardless of how high `final_score` is.**
- **`recommended` may only be `TRUE` if `final_score >= 6.0` AND both gates are `CONFIRMED`.** A gate at `REQUIRES_MANUAL_REVIEW` or `NOT_MEASURED` keeps the topic in `status = PENDING_HUMAN_REVIEW` — scored, but not yet clear to advance.
- Only a human reviewer may promote a gate to `CONFIRMED` (mirroring the same human-in-the-loop principle as [`03-visual-asset-rights-policy.md`](03-visual-asset-rights-policy.md) — AI-assisted research can surface evidence, but never self-certifies that sources or visual rights are good enough to proceed).

## Status lifecycle (`topic-registry.csv.status`)

`IDEA` → `PENDING_HUMAN_REVIEW` (scored, gates not yet confirmed) → `SOURCES_VERIFIED` (both gates `CONFIRMED`, ready for script drafting) → `SCRIPT_DRAFT` → `SCRIPT_APPROVED` → `IN_PRODUCTION` → `SHORTS_DERIVED` → `READY_TO_PUBLISH` → `PUBLISHED`, with `REJECTED`, `BLOCKED_NO_SOURCES`, and `BLOCKED_NO_VISUAL_RIGHTS` as terminal-until-re-reviewed states.

## Worked example: how the initial idea list was scored

The five topics seeded in this stage were found via real web research (Wikipedia, Eurostat, Wikimedia Commons), not invented. For each: `evergreen_score`, `source_availability_score`, `visual_rights_availability_score`, `production_ease_score`, and `monetization_safety_score` were assigned based on what was actually found (cited in `topic-scoring-log.csv`); `demand_score` and `competition_score` are `NOT_MEASURED`. Because 5 of 7 dimensions were measured (≥4), each `final_score` is a real computed average — but every topic still sits at `status = PENDING_HUMAN_REVIEW` because both gate fields are `REQUIRES_MANUAL_REVIEW`: the AI-assisted research found credible sources and confirmed Wikimedia Commons categories exist, but no human has yet verified them against [`03-visual-asset-rights-policy.md`](03-visual-asset-rights-policy.md) or logged them in [`source-registry.csv`](../templates/source-registry.csv) / [`visual-asset-registry.csv`](../templates/visual-asset-registry.csv). This is the expected, correct state for a freshly-researched topic — not a gap to paper over.
