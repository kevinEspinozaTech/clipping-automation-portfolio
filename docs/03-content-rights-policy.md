# 03 — Content Rights Policy

> **This policy is an operational process control, not legal advice.** It defines how this system decides whether a source video is allowed to enter automated processing. It does not replace a qualified legal review of copyright, licensing, or platform terms. See the disclaimer in the root [README.md](../README.md).

## Purpose

No source video may be transcribed, analyzed, clipped, or published by this system unless its commercial reuse rights have been explicitly verified by a human and recorded in [`templates/rights-registry.csv`](../templates/rights-registry.csv). This policy defines the required states, the advancement condition, what counts as valid authorization, what does not, and how multiple rights holders are handled.

## Required rights statuses

Every source must be in exactly one of these five states at all times:

| Status | Meaning |
|---|---|
| `PENDING_REVIEW` | Authorization has been requested or is being evaluated, but not yet confirmed. Default state for any new source. |
| `VERIFIED` | A human has confirmed, with documented evidence, that all required usage permissions are in place and current. |
| `REJECTED` | Authorization was explicitly denied, found insufficient, or determined not obtainable. |
| `EXPIRED` | Authorization was previously verified but its validity period has passed. |
| `REVOKED` | Authorization was previously verified but has since been withdrawn by the rights holder. |

Only `VERIFIED` sources may ever be eligible to advance. `EXPIRED` and `REVOKED` are terminal-until-re-verified states — a source in either state must go back through full re-verification (not be silently reactivated) before it can advance again.

## Advancement condition

A source may proceed past the rights gate **only if every one of the following is simultaneously true**:

```text
rights_status = VERIFIED
commercial_use_allowed = TRUE
editing_allowed = TRUE
platform_use_allowed = TRUE
authorization_expired = FALSE
human_review_completed = TRUE
```

If any single condition fails, the source must remain blocked. There is no partial-approval state and no automatic override.

## Acceptable sources of authorization

Authorization may be established only through one of the following, each documented with an `evidence_reference` in the rights registry (never the evidence itself — see [Evidence handling](#evidence-handling)):

- **Own content** — the user created and owns the video outright.
- **Written permission from the rights holder** — explicit written consent covering the intended use.
- **A contract or formal agreement** — e.g., a licensing or partnership agreement.
- **An explicit license compatible with modification and commercial use** — e.g., a Creative Commons license variant that permits commercial use and derivatives, or an equivalent explicit grant.
- **Confirmed public domain status** — verified, not assumed.

## What does NOT count as authorization

The following must never be treated as sufficient, individually or combined, to mark a source `VERIFIED`:

- The video being publicly viewable.
- The video being downloadable.
- The platform offering a native "Clip," "Share," "Embed," "Duet," "Stitch," or "Remix" feature.
- Other channels already having reused the same content.
- Crediting or attributing the original creator.
- The reused fragment being short.
- The creator not responding to an outreach request.
- Including a disclaimer such as "no copyright intended."
- Adding only superficial changes — subtitles, emojis, zoom effects, or background music.
- An automatic or informal interpretation of "fair use." Fair use (or equivalent doctrines) is a case-by-case legal determination, not a default state this system can apply.

Any source relying only on the items above must remain `PENDING_REVIEW` or move to `REJECTED` — it can never be marked `VERIFIED` on that basis alone.

## Multiple rights holders

A single piece of source content can implicate more than one independent rights holder, including but not limited to:

- The creator or streamer appearing in the video.
- The platform or production company that produced it.
- The owner of any music used in the video.
- The owner of any game, broadcast, or third-party footage shown in the video.
- Guests or participants appearing alongside the primary creator.
- Sponsors or other parties whose branded material appears in the video.

**If the status of any relevant rights holder is unclear, the source's overall `rights_status` must be `PENDING_REVIEW` or `REJECTED` — never `VERIFIED`.** Verification requires clarity across every relevant rights holder, not just the primary creator.

## Human review requirement

`human_review_completed` may only be set to `TRUE` by a named human reviewer (recorded in `verified_by`), after reviewing the actual evidence referenced by `evidence_reference`. This system does not, and will not, set this field automatically based on inferred signals, AI output, or the absence of an objection.

## Expiry and revocation handling

- Every `VERIFIED` record must have a `valid_from` date and, where applicable, an `expiry_date`.
- A source whose `expiry_date` has passed must be treated as `EXPIRED`, not `VERIFIED`, regardless of what the stored `rights_status` field currently says — expiry is evaluated at time of use, not only at time of entry.
- A source that a rights holder revokes must be moved to `REVOKED` immediately upon notice, with `revoked_at` recorded, and must stop advancing through the pipeline even if already `VERIFIED` moments earlier.

## Evidence handling

`evidence_reference` in the rights registry must contain only a fictitious identifier or a generic private-path reference (e.g., `private/agreements/source-0001.pdf`) — never the actual agreement, email, screenshot, or personal data. Real evidence belongs only in the local, git-ignored [`private/`](../private/README.md) folder, never in this repository's tracked history.
