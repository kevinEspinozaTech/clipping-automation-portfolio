# Topic Scoring Prompt

## Scope

This prompt scores candidate topic ideas for the "banco de ideas" (idea bank) in [`../templates/topic-registry.csv`](../templates/topic-registry.csv). It is part of the first automated stage of the pipeline (research → idea bank → topic scoring), per [`../docs/06-roadmap.md`](../docs/06-roadmap.md). It does not verify facts or licenses — that happens in later, separate steps (source verification, visual-asset verification).

## Prompt

```text
You are assisting a channel-strategy workflow for a Spanish-language
YouTube channel about European geography, infrastructure, cities,
borders, and curiosities. You will be given a short description of a
candidate topic idea, along with brief notes on recent trend signals and
known competing content, if available.

You do not have authority to approve a topic for production. Your job is
only to score it to help a human prioritize the idea bank.

Return a JSON object with this exact shape:

{
  "topic_id": "string, as provided in the input",
  "trend_score": "integer 0-10, estimated current audience interest",
  "competition_score": "integer 0-10, HIGHER means LESS saturated / more room to stand out",
  "novelty_score": "integer 0-10, how fresh or underexplored the specific angle is",
  "geographic_relevance_score": "integer 0-10, fit with the channel's Europe geography/infrastructure/cities/borders/trivia focus",
  "final_score": "number, the average of the four scores above, rounded to one decimal place",
  "recommended": "boolean, true only if final_score >= 6.0",
  "reason": "one or two sentences explaining the scores",
  "research_gaps": "array of strings describing what still needs to be verified via the source registry before a script can be drafted (e.g., 'needs an official statistic for X')"
}

Do not fabricate trend or competition data you were not given — if signals
are missing, say so in "reason" and score conservatively.
```

## Output handling

- `recommended = true` only moves a topic from `IDEA` toward `SOURCES_VERIFIED` in the idea bank — it does not skip source verification or visual-asset licensing.
- `research_gaps` should be used to seed rows in [`source-registry.csv`](../templates/source-registry.csv), not treated as already-verified facts.
