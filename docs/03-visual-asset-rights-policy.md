# 03 — Visual Asset Rights Policy

> **This policy is an operational process control, not legal advice.** It defines how this system decides whether an individual visual or audio asset (map, photo, stock footage clip, chart, music track, sound effect) may be used inside an original video. It does not replace a qualified legal review of copyright or licensing terms. See the disclaimer in the root [README.md](../README.md).
>
> See [`decisions/ADR-001-pivot-to-original-faceless-content.md`](decisions/ADR-001-pivot-to-original-faceless-content.md) for why this policy replaced the Stage 1 whole-video reuse policy.

## Purpose

This project produces **original** video content. It does not reuse other creators' whole videos. It does, however, use individual supporting assets — maps, photographs, stock footage, charts, background music — inside otherwise-original videos. No such asset may be used in an edited or published video unless its license has been explicitly verified by a human and recorded in [`../templates/visual-asset-registry.csv`](../templates/visual-asset-registry.csv).

## License taxonomy

Every visual/audio asset must be classified into exactly one of these seven categories:

| `license_type` | Meaning |
|---|---|
| `ORIGINAL` | Created from scratch for this project (e.g., a custom-generated map, an in-house graphic, an AI-generated illustration with commercial-use terms confirmed). |
| `OWN_MATERIAL` | Owned by the project/creator outright (e.g., personally shot footage or photos). |
| `PUBLIC_DOMAIN` | Confirmed public domain — not assumed. |
| `CREATIVE_COMMONS_COMPATIBLE` | Under a Creative Commons (or equivalent) license that explicitly permits commercial use and modification. |
| `LICENSED` | Obtained through a paid or formal license (e.g., a stock footage/music subscription with commercial terms). |
| `DIRECT_PERMISSION` | Explicit written permission obtained directly from the rights holder for this specific use. |
| `UNAUTHORIZED` | No valid basis established. Always blocks use — this classification exists so an asset can be logged and rejected rather than silently dropped. |

## Required approval statuses

Every asset record also carries an approval status, unchanged from the Stage 1 lifecycle:

| Status | Meaning |
|---|---|
| `PENDING_REVIEW` | Under evaluation. Default for any newly logged asset. |
| `VERIFIED` | A human has confirmed the license classification and evidence, and the asset may be used within its documented scope. |
| `REJECTED` | Determined unusable (e.g., classified `UNAUTHORIZED`, or license terms don't cover the intended use). |
| `EXPIRED` | A previously `VERIFIED` license's validity period has passed. |
| `REVOKED` | A previously `VERIFIED` license has been withdrawn. |

## Mandatory fields — no asset advances without all eight

Per the project's acceptance criteria, an asset can never be used in production unless **every one** of the following fields is populated in `visual-asset-registry.csv`:

1. `source` — where the asset comes from.
2. `author` — the creator/rights holder.
3. `license_type` — one of the seven categories above.
4. `source_url` — the original URL or reference.
5. `verified_at` — date the license was checked.
6. `allowed_scope` — what the license actually permits (e.g., "commercial, modified, any platform" or "editorial use only, no modification").
7. `evidence_reference` — a fictitious identifier or generic private path pointing to the real evidence, which itself is never committed (see [Evidence handling](#evidence-handling)).
8. `approval_status` — must be `VERIFIED` for the asset to be usable.

## Advancement condition

An asset may be used in an edited video only if:

```text
approval_status = VERIFIED
license_type != UNAUTHORIZED
all 8 mandatory fields above are populated
human_review_completed = TRUE
```

If any condition fails, the asset stays blocked and must not appear in a rendered video.

## What does NOT count as sufficient basis for `VERIFIED`

Carried forward unchanged from the Stage 1 policy, applied now to individual assets instead of whole videos:

- The asset being publicly viewable or easy to find via search/image search.
- The asset being downloadable.
- A platform offering a "free to use," "royalty-free"-sounding label without checking the actual license text.
- Other channels already using similar assets.
- Crediting the original author being treated as a substitute for actually having a compatible license.
- The excerpt/crop being small.
- The author not responding to an outreach request.
- An informal or automatic interpretation of "fair use."

## Evidence handling

`evidence_reference` must contain only a fictitious identifier or a generic private-path reference (e.g., `private/licenses/asset-0001.pdf`) — never the actual license file, receipt, or correspondence. Real evidence belongs only in the local, git-ignored [`private/`](../private/README.md) folder.

## Human review requirement

`human_review_completed` may only be set `TRUE` by a named reviewer after checking the actual evidence. It is never inferred from AI output or from the absence of an objection — consistent with the project's overall human-in-the-loop principle (see [README.md](../README.md)).
