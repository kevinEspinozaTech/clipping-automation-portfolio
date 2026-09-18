# 04 — Data Dictionary

This document defines every field used in the CSV registries under [`templates/`](../templates/) and [`results/`](../results/). All example rows in those files are fictitious and marked as examples.

## `topic-registry.csv`

The idea bank. Per-dimension scores and their evidence live separately in [`topic-scoring-log.csv`](#topic-scoring-logcsv) — see [`07-topic-scoring-methodology.md`](07-topic-scoring-methodology.md) for how `final_score` is computed from that log.

| Field | Type | Description |
|---|---|---|
| `topic_id` | string | Unique identifier for the topic idea (e.g., `TOPIC-0001`). |
| `working_title` | string | Draft working title for the video. |
| `category` | enum | `geography`, `infrastructure`, `cities`, `borders`, `curiosities` (extendable). |
| `region` | string | Geographic region focus (initially always `Europe`). |
| `language` | string | Target language (ISO 639-1, initially always `es`). |
| `sources_available_status` | enum | `NOT_MEASURED`, `REQUIRES_MANUAL_REVIEW`, `CONFIRMED`, `INSUFFICIENT`. Hard gate — see methodology. |
| `visual_resources_feasible_status` | enum | Same enum as above. Hard gate — see methodology. |
| `final_score` | number or `REQUIRES_MANUAL_REVIEW` | Weighted mean of whichever of the 7 scoring dimensions in `topic-scoring-log.csv` are real numbers; `REQUIRES_MANUAL_REVIEW` if fewer than 4 of 7 are measured. |
| `recommended` | boolean | `TRUE` only if `final_score >= 6.0` AND both gate fields are `CONFIRMED`. |
| `status` | enum | `IDEA`, `PENDING_HUMAN_REVIEW`, `SOURCES_VERIFIED`, `SCRIPT_DRAFT`, `SCRIPT_APPROVED`, `IN_PRODUCTION`, `SHORTS_DERIVED`, `READY_TO_PUBLISH`, `PUBLISHED`, `REJECTED`, `BLOCKED_NO_SOURCES`, `BLOCKED_NO_VISUAL_RIGHTS`, `BLOCKED_INVALID_INTAKE`. |
| `created_at` | date | Date the topic was logged. |
| `last_scored_at` | date | Date `final_score` was last (re)computed. |
| `notes` | string | Free-text internal notes. |

## `topic-scoring-log.csv`

The auditable evidence trail behind every `final_score` — one row per scored dimension per topic. See [`07-topic-scoring-methodology.md`](07-topic-scoring-methodology.md) for the full formula and the no-fabrication rule.

| Field | Type | Description |
|---|---|---|
| `log_id` | string | Unique identifier for this scoring entry (e.g., `LOG-0001`). |
| `topic_id` | string | Foreign key to `topic-registry.csv`. |
| `dimension` | enum | `demand_score`, `competition_score`, `evergreen_score`, `source_availability_score`, `visual_rights_availability_score`, `production_ease_score`, `monetization_safety_score`. |
| `value_or_status` | number (0-10) or string | A real score, or the literal string `NOT_MEASURED` — never a fabricated number. |
| `weight` | string | Weight used for this dimension in the formula (default `1/7`, adjustable). |
| `source` | string | Description of where the value came from (external source, or an internal editorial judgment call, stated honestly either way). |
| `source_url` | string | URL of the source, if external. Empty if none. |
| `consulted_at` | date | Date the source was consulted. Empty if not applicable (e.g., `NOT_MEASURED`). |
| `scored_by` | string | Who/what produced this entry (e.g., `AI-assisted (Claude) -- pending human review`). |
| `scored_at` | date | Date this log entry was created. |
| `notes` | string | Justification for the value, or why it is `NOT_MEASURED`. |

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
