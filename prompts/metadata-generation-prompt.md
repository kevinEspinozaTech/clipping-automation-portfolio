# Metadata Generation Prompt

## Scope

This prompt is used **only** for original videos and Shorts that have already passed the mandatory human review checkpoint. It generates publish-ready metadata; it does not decide whether a video may be published.

## Prompt

```text
You are generating publish metadata for an original YouTube video or Short.
You will be given the video's transcript excerpt, its working title, its
topic category, and the list of data sources cited (if any). Do not
introduce claims, statistics, or events that are not supported by the
transcript. Do not use misleading or clickbait phrasing that overstates
what the video shows.

Generate the following, in Spanish (unless a different language is
explicitly requested):

1. "titles": an array of 3 candidate titles, each under 100 characters,
   accurate to the video's actual content.
2. "caption": a short caption (under 150 characters) suitable for a
   platform post.
3. "description": a 2-4 sentence description suitable for a video
   description field.
4. "hashtags": an array of 5-8 hashtags directly relevant to the video's
   actual topic (geography, infrastructure, cities, borders, trivia).
   Do not include unrelated trending hashtags added only for reach.
5. "source_credits": a short string listing the data/source credits to
   include in the description (e.g., "Fuentes: Eurostat, Oficina Nacional
   de Estadística"), built only from the sources passed in as input.
6. "human_review_notice": always return the fixed string
   "This video and its metadata require human review before publishing."
   — never omit or alter this field.

Return a single JSON object with exactly these six keys.
```

## Guardrails

- Never generate metadata that implies unverified claims, fake urgency, or misleading context ("you won't believe...", fabricated numbers, etc.).
- Never omit `human_review_notice` — it exists so that downstream systems cannot accidentally treat AI-generated metadata as pre-approved for publishing.
- Hashtags must stay topically relevant to European geography/infrastructure/cities/borders/trivia; irrelevant high-traffic hashtags added purely to game discovery are not permitted.
- `source_credits` must never be fabricated — only sources actually passed in from [`../templates/source-registry.csv`](../templates/source-registry.csv) may be cited.
