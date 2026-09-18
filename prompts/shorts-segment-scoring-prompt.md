# Shorts Segment Scoring Prompt

## Scope

This prompt is used **only** against the transcript of the project's **own, original** long-form video — never a third-party video. It identifies which moments of an already-produced original video work well as standalone Shorts.

## Important limitation

**This prompt does not determine legality or factual accuracy.** It scores narrative/engagement qualities only. Any concern about a factual claim, an unverified statistic, or a visual asset used in the segment must still be checked against [`../docs/03-visual-asset-rights-policy.md`](../docs/03-visual-asset-rights-policy.md) and the source registry — those checks happen upstream, before this prompt runs, and are not re-validated here.

## Prompt

```text
You are assisting a video production workflow. The transcript provided
below is from an ORIGINAL video already produced by this project — you
are not evaluating third-party content. Your task is to identify and
score candidate segments for derived Shorts.

You do not have authority to approve publishing. If anything in the
segment references a visual/audio asset, a statistic, or a claim that
seems unverified or inconsistent with the rest of the script, set
content_flag to true and explain why in "reason" — do not attempt to
resolve it yourself.

For each candidate segment, return a JSON object with this exact shape:

{
  "segment_id": "string, unique within this transcript",
  "start_time": "HH:MM:SS",
  "end_time": "HH:MM:SS",
  "hook_score": "integer 0-10, strength of the opening 3 seconds",
  "clarity_score": "integer 0-10, how easy the segment is to follow without context",
  "emotion_score": "integer 0-10, emotional or curiosity-driven engagement",
  "standalone_score": "integer 0-10, how well the segment works without the rest of the video",
  "brand_safety_score": "integer 0-10, 10 = no concerning content",
  "content_flag": "boolean, true if ANY unverified claim or unresolved asset concern is detected in this segment",
  "recommended": "boolean, true only if hook_score >= 6 AND clarity_score >= 6 AND standalone_score >= 6 AND content_flag = false",
  "reason": "one or two sentences explaining the scores and, if applicable, the content concern"
}

Return an array of these objects, one per candidate segment, ordered by
start_time. Do not include segments shorter than 15 seconds or longer than
90 seconds. Do not fabricate timestamps or content not present in the
transcript.
```

## Output handling

- Any object with `content_flag = true` must be routed to human review and excluded from automatic recommendation, even if other scores are high.
- `recommended = true` is a suggestion for a human reviewer to prioritize, not an approval to publish — the mandatory final human review checkpoint still applies to every Short.
