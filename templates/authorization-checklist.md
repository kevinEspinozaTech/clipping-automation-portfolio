# Authorization Checklist

Use this checklist when reviewing a source before setting `rights_status = VERIFIED` in [`rights-registry.csv`](rights-registry.csv). This checklist supports, but does not replace, the full policy in [`../docs/03-content-rights-policy.md`](../docs/03-content-rights-policy.md). It is a review aid, not a legal determination.

## Before marking VERIFIED, confirm all of the following

- [ ] The rights holder's identity has been confirmed (not assumed from a channel name or handle).
- [ ] Every relevant rights holder has been identified — creator/streamer, platform/producer, music owner, game/broadcast owner, any guests, any sponsors — and each one's status is accounted for.
- [ ] Authorization is documented via one of the accepted sources: own content, written permission, contract/agreement, explicit compatible license, or confirmed public domain status.
- [ ] `commercial_use_allowed` is explicitly confirmed TRUE (not inferred).
- [ ] `editing_allowed` is explicitly confirmed TRUE (not inferred).
- [ ] `platform_use_allowed` is explicitly confirmed TRUE for each platform in `allowed_platforms`.
- [ ] `authorization_expired` is FALSE as of today, and `expiry_date` (if any) is recorded.
- [ ] `evidence_reference` points to a private, non-versioned location — the actual evidence is never committed to this repository.
- [ ] A named human reviewer has completed the review and is recorded in `verified_by`.
- [ ] `human_review_completed` is set to TRUE only after the above steps, not before.

## Automatic disqualifiers — stop and do NOT mark VERIFIED if any apply

- [ ] The only basis for reuse is that the video is public or downloadable.
- [ ] The only basis for reuse is a platform "Clip / Share / Remix / Duet / Stitch" feature.
- [ ] The only basis for reuse is that other channels already reuse similar content.
- [ ] The only basis for reuse is crediting the creator.
- [ ] The only basis for reuse is that the creator has not responded.
- [ ] The only basis for reuse is a "no copyright intended" disclaimer.
- [ ] The only change planned is superficial (subtitles, emojis, zoom, background music).
- [ ] The only basis for reuse is an informal "fair use" judgment.

If any disqualifier applies and no accepted authorization source also exists, set `rights_status` to `PENDING_REVIEW` (if still being pursued) or `REJECTED` (if denied or not obtainable).

## Ongoing monitoring

- [ ] Recheck `expiry_date` before every reuse of a previously `VERIFIED` source, not only at intake.
- [ ] If a rights holder revokes permission, immediately set `rights_status = REVOKED`, record `revoked_at`, and stop further use.
