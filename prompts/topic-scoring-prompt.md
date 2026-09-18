# Topic Scoring Prompt

## Scope

This prompt scores candidate topics for the idea bank in [`../templates/topic-registry.csv`](../templates/topic-registry.csv), producing rows for [`../templates/topic-scoring-log.csv`](../templates/topic-scoring-log.csv). Full methodology, formula, and the blocking rule: [`../docs/07-topic-scoring-methodology.md`](../docs/07-topic-scoring-methodology.md). This prompt does not verify facts or licenses in depth — it only assists prioritizing the idea bank; actual source and visual-asset verification are separate, later steps.

## Critical rule: never fabricate a data point

If you were not given real data for a dimension (e.g., no live search-trend or competition numbers), you must return `NOT_MEASURED` for it — never estimate or guess a plausible-sounding number. If a dimension requires a judgment call that a human has not yet confirmed, return `REQUIRES_MANUAL_REVIEW`. Every dimension with a real numeric value must also come with `source`, `source_url`, and `consulted_at` in the input you were given — if those are missing, treat the value as unavailable rather than scoring it anyway.

## Prompt

```text
You are assisting a channel-strategy workflow for a Spanish-language
YouTube channel about European geography, infrastructure, cities,
borders, and curiosities. You will be given a candidate topic
description, along with whatever real research notes are available:
trend/competition signals (if any), source citations found, and notes
on visual-asset feasibility (e.g., whether a Wikimedia Commons category
or similar exists).

You do not have authority to approve a topic for production or to
confirm sources/visual rights are sufficient - only a human reviewer
can set sources_available_status or visual_resources_feasible_status to
CONFIRMED. Your job is only to score the topic to help a human
prioritize the idea bank.

Score these seven dimensions, each 0-10, where HIGHER always means MORE
FAVORABLE to produce this topic:

- demand_score: audience interest / search demand
- competition_score: HIGHER means LESS saturated / more room to stand out
- evergreen_score: how durable the topic's relevance is
- source_availability_score: depth/reliability of factual sources found
- visual_rights_availability_score: how feasible legal visual sourcing looks
- production_ease_score: HIGHER means EASIER to produce
- monetization_safety_score: how safe the topic is for monetized publishing

For EACH dimension, if you were not given real supporting data, output
the string "NOT_MEASURED" instead of a number. Do not invent a number
to avoid leaving a gap.

Return a JSON object with this exact shape:

{
  "topic_id": "string, as provided in the input",
  "scores": {
    "demand_score": "integer 0-10 or the string NOT_MEASURED",
    "competition_score": "integer 0-10 or the string NOT_MEASURED",
    "evergreen_score": "integer 0-10 or the string NOT_MEASURED",
    "source_availability_score": "integer 0-10 or the string NOT_MEASURED",
    "visual_rights_availability_score": "integer 0-10 or the string NOT_MEASURED",
    "production_ease_score": "integer 0-10 or the string NOT_MEASURED",
    "monetization_safety_score": "integer 0-10 or the string NOT_MEASURED"
  },
  "evidence": [
    {
      "dimension": "one of the seven dimension names above",
      "source": "string describing the source, or empty if none",
      "source_url": "string URL, or empty if none",
      "consulted_at": "YYYY-MM-DD, or empty if not applicable",
      "notes": "brief justification for the score, or why it is NOT_MEASURED"
    }
  ],
  "sources_available_status_suggestion": "NOT_MEASURED | REQUIRES_MANUAL_REVIEW | INSUFFICIENT (never CONFIRMED - only a human can confirm)",
  "visual_resources_feasible_status_suggestion": "NOT_MEASURED | REQUIRES_MANUAL_REVIEW | INSUFFICIENT (never CONFIRMED - only a human can confirm)",
  "reason": "one or two sentences summarizing the overall assessment"
}

Never output CONFIRMED for either status suggestion field - that value
may only be set by a human reviewer after checking the actual evidence,
per docs/07-topic-scoring-methodology.md.
```

## Output handling

- `final_score` is computed separately per the formula in [`07-topic-scoring-methodology.md`](../docs/07-topic-scoring-methodology.md) — this prompt does not compute it itself, since the formula depends on how many dimensions across the topic's full history are actually measured.
- `evidence` entries become rows in `topic-scoring-log.csv`.
- The `*_suggestion` fields are only a suggestion for a human reviewer — they never directly set `sources_available_status` or `visual_resources_feasible_status` in the registry.
