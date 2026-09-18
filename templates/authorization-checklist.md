# Authorization Checklist (Visual/Audio Asset)

Use this checklist when reviewing an asset before setting `approval_status = VERIFIED` in [`visual-asset-registry.csv`](visual-asset-registry.csv). This checklist supports, but does not replace, the full policy in [`../docs/03-visual-asset-rights-policy.md`](../docs/03-visual-asset-rights-policy.md). It is a review aid, not a legal determination.

## Before marking VERIFIED, confirm all of the following

- [ ] The asset's rights holder/author has been confirmed (not assumed from a filename or upload account).
- [ ] `license_type` is correctly classified as one of: `ORIGINAL`, `OWN_MATERIAL`, `PUBLIC_DOMAIN`, `CREATIVE_COMMONS_COMPATIBLE`, `LICENSED`, `DIRECT_PERMISSION`. (If it would be `UNAUTHORIZED`, stop — it cannot be `VERIFIED`.)
- [ ] `source`, `author`, `source_url`, `verified_at`, `allowed_scope`, and `evidence_reference` are all populated — no mandatory field is blank.
- [ ] `allowed_scope` explicitly covers commercial use and the intended modification (crop, recolor, edit, overlay text, etc.).
- [ ] `allowed_scope` explicitly covers every platform the resulting video will be published to.
- [ ] `evidence_reference` points to a private, non-versioned location — the actual license/evidence is never committed to this repository.
- [ ] A named human reviewer has completed the review, and `human_review_completed` is set to TRUE only after the above steps.

## Automatic disqualifiers — stop and do NOT mark VERIFIED if any apply

- [ ] The only basis for use is that the asset is easy to find via a search engine or image search.
- [ ] The only basis for use is a "free to use" / "royalty-free" label without checking the actual license terms.
- [ ] The only basis for use is that other channels already use similar assets.
- [ ] The only basis for use is crediting the original author, without a compatible license.
- [ ] The only basis for use is that the author has not responded to an outreach request.
- [ ] The only basis for use is an informal "fair use" judgment.

If any disqualifier applies and no accepted license category also exists, classify the asset `UNAUTHORIZED` and set `approval_status` to `REJECTED` (or `PENDING_REVIEW` if still being pursued through direct permission).

## Ongoing monitoring

- [ ] Recheck any `expiry_date`-equivalent terms before reusing a previously `VERIFIED` asset in a new video.
- [ ] If a rights holder revokes permission, immediately set `approval_status = REVOKED` and remove the asset from any video not yet published.
