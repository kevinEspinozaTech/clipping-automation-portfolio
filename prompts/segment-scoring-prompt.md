# Segment Scoring Prompt

## Scope

This prompt is used **only** against transcripts of sources whose `rights_status = VERIFIED` in [`../templates/rights-registry.csv`](../templates/rights-registry.csv), per [`../docs/03-content-rights-policy.md`](../docs/03-content-rights-policy.md). It must never be run against a transcript from a blocked, pending, expired, or revoked source.

## Important limitation

**This prompt does not determine legality.** `rights_risk_flag` below is a best-effort signal based only on what the transcript itself says (e.g., an unannounced sponsorship mention, a reference to unlicensed third-party music, a guest explicitly objecting to reuse). It is not a substitute for the human rights-verification process. Any `rights_risk_flag = true` output must force human review before the segment is used further, regardless of the source's existing `VERIFIED` status.

## Prompt

```text
You are assisting a video production workflow that has already confirmed
commercial reuse rights for the transcript provided below. Your task is to
identify and score candidate segments for short vertical clips.

You do not have authority to approve or reject content on legal or rights
grounds. If anything in the transcript suggests a rights concern (e.g. an
unlicensed music mention, an unannounced sponsor read, a guest objecting to
reuse, reference to someone else's unreleased or private content), set
rights_risk_flag to true and explain why in "reason" — do not attempt to
resolve it yourself.

For each candidate segment, return a JSON object with this exact shape:

{
  "segment_id": "string, unique within this transcript",
  "start_time": "HH:MM:SS",
  "end_time": "HH:MM:SS",
  "hook_score": "integer 0-10, strength of the opening 3 seconds",
  "clarity_score": "integer 0-10, how easy the segment is to follow without context",
  "emotion_score": "integer 0-10, emotional engagement/energy",
  "standalone_score": "integer 0-10, how well the segment works without the rest of the video",
  "brand_safety_score": "integer 0-10, 10 = no concerning content",
  "rights_risk_flag": "boolean, true if ANY rights concern is detected in this segment",
  "recommended": "boolean, true only if hook_score >= 6 AND clarity_score >= 6 AND standalone_score >= 6 AND rights_risk_flag = false",
  "reason": "one or two sentences explaining the scores and, if applicable, the rights concern"
}

Return an array of these objects, one per candidate segment, ordered by
start_time. Do not include segments shorter than 15 seconds or longer than
90 seconds. Do not fabricate timestamps or content not present in the
transcript.
```

## Output handling

- Any object with `rights_risk_flag = true` must be routed to human review and excluded from automatic recommendation, even if other scores are high.
- `recommended = true` is a suggestion for a human reviewer to prioritize, not an approval to publish — the mandatory human review checkpoint (Stage 7 of the roadmap) still applies to every segment.
