# Metadata Generation Prompt

## Scope

This prompt is used **only** for segments already scored and recommended by [`segment-scoring-prompt.md`](segment-scoring-prompt.md) from a `VERIFIED` source, and only after the mandatory human review checkpoint. It generates publish-ready metadata; it does not decide whether a clip may be published.

## Prompt

```text
You are generating publish metadata for a short vertical video clip. You
will be given the clip's transcript excerpt, its source title, and its
required attribution text (if any). Do not introduce claims, statistics, or
events that are not supported by the transcript excerpt. Do not use
misleading or clickbait phrasing that overstates what the clip shows.

Generate the following, in the same language as the transcript excerpt:

1. "titles": an array of 3 candidate titles, each under 100 characters,
   accurate to the clip's actual content.
2. "caption": a short caption (under 150 characters) suitable for a
   platform post.
3. "description": a 2-4 sentence description suitable for a video
   description field.
4. "hashtags": an array of 5-8 hashtags directly relevant to the clip's
   actual topic, niche, or content type. Do not include unrelated
   trending hashtags added only for reach.
5. "attribution_text": the exact attribution string to include if
   attribution_required = true for this source (passed in as input);
   otherwise return an empty string.
6. "human_review_notice": always return the fixed string
   "This clip and its metadata require human review and rights
   confirmation before publishing." — never omit or alter this field.

Return a single JSON object with exactly these six keys.
```

## Guardrails

- Never generate metadata that implies unverified claims, fake urgency, or misleading context ("you won't believe...", fabricated numbers, etc.).
- Never omit `human_review_notice` — it exists so that downstream systems cannot accidentally treat AI-generated metadata as pre-approved for publishing.
- Hashtags must stay topically relevant; irrelevant high-traffic hashtags added purely to game discovery are not permitted.
- If `attribution_required = true` in the source's rights record, `attribution_text` must never be left empty.
