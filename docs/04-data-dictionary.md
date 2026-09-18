# 04 — Data Dictionary

This document defines every field used in the CSV registries under [`templates/`](../templates/) and [`results/`](../results/). All example rows in those files are fictitious and marked as examples.

## `content-registry.csv`

| Field | Type | Description |
|---|---|---|
| `source_id` | string | Unique identifier for the source video (e.g., `SRC-0001`). |
| `source_url` | string | Reference URL of the source (for internal tracking only — does not imply authorization). |
| `source_platform` | string | Platform the source was found on (e.g., YouTube, Twitch). |
| `creator_name` | string | Name of the primary creator or channel. |
| `video_title` | string | Title of the source video. |
| `published_at` | date | Original publish date of the source video. |
| `duration_seconds` | integer | Length of the source video in seconds. |
| `language` | string | Primary spoken language (ISO 639-1 code, e.g., `en`, `es`). |
| `niche` | string | Content category/niche (e.g., "gaming", "education"). |
| `intake_date` | date | Date the source was registered in this system. |
| `rights_status` | enum | One of `PENDING_REVIEW`, `VERIFIED`, `REJECTED`, `EXPIRED`, `REVOKED` — mirrors `rights-registry.csv`. |
| `processing_status` | enum | Pipeline stage, e.g., `INTAKE`, `BLOCKED`, `READY_FOR_TRANSCRIPTION`, `TRANSCRIBED`, `SCORED`, `CLIPPED`, `PUBLISHED`. |
| `notes` | string | Free-text internal notes. |

## `rights-registry.csv`

| Field | Type | Description |
|---|---|---|
| `source_id` | string | Foreign key to `content-registry.csv`. |
| `rights_holder` | string | Name/entity of the rights holder this record covers. |
| `authorization_type` | enum | `OWN_CONTENT`, `WRITTEN_PERMISSION`, `CONTRACT`, `EXPLICIT_LICENSE`, `PUBLIC_DOMAIN_CONFIRMED`. |
| `commercial_use_allowed` | boolean | Whether commercial use is explicitly permitted. |
| `editing_allowed` | boolean | Whether editing/derivative works are explicitly permitted. |
| `platform_use_allowed` | boolean | Whether use on the intended target platforms is explicitly permitted. |
| `allowed_platforms` | string | Semicolon-separated list of platforms authorization covers (e.g., `YouTube Shorts;TikTok`). |
| `attribution_required` | boolean | Whether attribution to the rights holder is required. |
| `evidence_reference` | string | Fictitious identifier or generic private path — never real evidence (see [content-rights-policy](03-content-rights-policy.md#evidence-handling)). |
| `verified_by` | string | Name/role of the human reviewer who completed verification. |
| `verified_at` | date | Date verification was completed. |
| `valid_from` | date | Date authorization becomes effective. |
| `expiry_date` | date (nullable) | Date authorization expires, if applicable. |
| `revoked_at` | date (nullable) | Date authorization was revoked, if applicable. |
| `human_review_completed` | boolean | Whether the mandatory human review step was completed. |
| `rights_status` | enum | One of `PENDING_REVIEW`, `VERIFIED`, `REJECTED`, `EXPIRED`, `REVOKED`. |
| `notes` | string | Free-text internal notes. |

## `performance-metrics.csv`

| Field | Type | Description |
|---|---|---|
| `clip_id` | string | Unique identifier for a published clip. |
| `source_id` | string | Foreign key to `content-registry.csv`. |
| `platform` | string | Platform the clip was published to. |
| `published_at` | date | Publish date/time of the clip. |
| `views_24h` | integer | Views in the first 24 hours. |
| `views_7d` | integer | Views in the first 7 days. |
| `average_watch_time` | number | Average watch time in seconds. |
| `completion_rate` | number | Fraction (0–1) of viewers who watched to completion. |
| `likes` | integer | Total likes. |
| `comments` | integer | Total comments. |
| `shares` | integer | Total shares. |
| `saves` | integer | Total saves/bookmarks. |
| `followers_gained` | integer | Estimated followers gained attributable to the clip. |
| `rights_status_at_publish` | enum | Rights status recorded at the moment of publishing, for auditability. |
| `notes` | string | Free-text internal notes. |

## `results/sample-results.csv`

A demonstrative, fictitious extract combining fields from the registries above to illustrate what a reporting export might look like. It is explicitly not real production data.
