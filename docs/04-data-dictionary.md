# 04 — Data Dictionary

This document defines every field used in the CSV registries under [`templates/`](../templates/) and [`results/`](../results/). All example rows in those files are fictitious and marked as examples.

## `topic-registry.csv`

| Field | Type | Description |
|---|---|---|
| `topic_id` | string | Unique identifier for the topic idea (e.g., `TOPIC-0001`). |
| `working_title` | string | Draft working title for the video. |
| `category` | enum | `geography`, `infrastructure`, `cities`, `borders`, `curiosities` (extendable). |
| `region` | string | Geographic region focus (initially always `Europe`). |
| `language` | string | Target language (ISO 639-1, initially always `es`). |
| `trend_score` | number (0-10) | Estimated current audience interest. |
| `competition_score` | number (0-10) | Higher = less saturated / more room to stand out. |
| `novelty_score` | number (0-10) | How fresh or underexplored the angle is. |
| `final_score` | number | Average of the score fields above (see [`prompts/topic-scoring-prompt.md`](../prompts/topic-scoring-prompt.md)). |
| `status` | enum | `IDEA`, `SOURCES_VERIFIED`, `SCRIPT_DRAFT`, `SCRIPT_APPROVED`, `IN_PRODUCTION`, `SHORTS_DERIVED`, `READY_TO_PUBLISH`, `PUBLISHED`, `REJECTED`. |
| `created_at` | date | Date the topic was logged. |
| `notes` | string | Free-text internal notes. |

## `source-registry.csv`

| Field | Type | Description |
|---|---|---|
| `source_id` | string | Unique identifier for the research source. |
| `topic_id` | string | Foreign key to `topic-registry.csv`. |
| `source_url` | string | Reference URL of the source. |
| `source_type` | enum | `official_statistics`, `news`, `academic`, `encyclopedia`, `government`, `other`. |
| `publisher` | string | Name of the publishing organization. |
| `accessed_at` | date | Date the source was accessed/reviewed. |
| `reliability_notes` | string | Notes on how the source was cross-checked or its reliability. |
| `verified_by` | string | Name/role of the human reviewer who confirmed the source. |
| `verified_at` | date | Date verification was completed. |
| `notes` | string | Free-text internal notes. |

## `visual-asset-registry.csv`

The 8 fields marked **mandatory** below are required before any asset may be used, per [`03-visual-asset-rights-policy.md`](03-visual-asset-rights-policy.md).

| Field | Type | Mandatory | Description |
|---|---|---|---|
| `asset_id` | string | yes (implicit key) | Unique identifier for the asset. |
| `topic_id` | string | | Foreign key to `topic-registry.csv`. |
| `asset_type` | enum | | `map`, `photo`, `footage`, `chart`, `music`, `other`. |
| `source` | string | **yes** | Where the asset comes from. |
| `author` | string | **yes** | The creator/rights holder. |
| `license_type` | enum | **yes** | `ORIGINAL`, `OWN_MATERIAL`, `PUBLIC_DOMAIN`, `CREATIVE_COMMONS_COMPATIBLE`, `LICENSED`, `DIRECT_PERMISSION`, `UNAUTHORIZED`. |
| `source_url` | string | **yes** | Original URL or reference (may be empty only for `ORIGINAL`/`OWN_MATERIAL`). |
| `verified_at` | date | **yes** | Date the license was checked. |
| `allowed_scope` | string | **yes** | What the license actually permits. |
| `evidence_reference` | string | **yes** | Fictitious identifier or generic private path — never real evidence. |
| `approval_status` | enum | **yes** | `PENDING_REVIEW`, `VERIFIED`, `REJECTED`, `EXPIRED`, `REVOKED`. |
| `human_review_completed` | boolean | | Whether the mandatory human review step was completed. |
| `notes` | string | | Free-text internal notes. |

## `performance-metrics.csv`

| Field | Type | Description |
|---|---|---|
| `video_id` | string | Unique identifier for a published video or Short. |
| `topic_id` | string | Foreign key to `topic-registry.csv`. |
| `video_type` | enum | `long_form`, `short`. |
| `platform` | string | Platform the video was published to. |
| `published_at` | date | Publish date/time. |
| `views_24h` | integer | Views in the first 24 hours. |
| `views_7d` | integer | Views in the first 7 days. |
| `average_view_duration` | number | Average view duration in seconds. |
| `completion_rate` | number | Fraction (0-1) of viewers who watched to completion. |
| `likes` | integer | Total likes. |
| `comments` | integer | Total comments. |
| `shares` | integer | Total shares. |
| `saves` | integer | Total saves/bookmarks. |
| `subscribers_gained` | integer | Estimated subscribers gained attributable to the video. |
| `assets_cleared_at_publish` | boolean | Whether every visual/audio asset used was `VERIFIED` at publish time, for auditability. |
| `notes` | string | Free-text internal notes. |

## `results/sample-results.csv`

A demonstrative, fictitious extract combining fields from the registries above to illustrate what a reporting export might look like. It is explicitly not real production data.
