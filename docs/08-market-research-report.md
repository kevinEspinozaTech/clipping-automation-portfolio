# 08 — Market Research Report: Faceless YouTube Niches & Formats (Stage 2B)

**Research date:** 2026-09-18. **Scope:** 8 candidate niche families, 16 real comparable channels/videos, scored on 10 criteria. Full evidence trail: [`../templates/channel-video-registry.csv`](../templates/channel-video-registry.csv) (dossiers) and [`../templates/niche-scoring-matrix.csv`](../templates/niche-scoring-matrix.csv) (per-criterion scores + sources). Methodology: [`09-niche-scoring-methodology.md`](09-niche-scoring-methodology.md). This report does not select a final niche — see [`decisions/ADR-002-niche-format-shortlist-pending-decision.md`](decisions/ADR-002-niche-format-shortlist-pending-decision.md) for the provisional shortlist and non-binding recommendation.

## Methodology summary

For each of 8 niche families, 2 real channels/videos were identified via public web search and, where possible, official/primary sources (e.g., a channel's own site, YouTube's own policy pages). Every dossier records only what could actually be observed or reasonably cited — a real subscriber/view count with its source, or `NOT_PUBLICLY_AVAILABLE` where no public figure could be found. No RPM, revenue, retention, or internal competition metric was ever estimated or invented; where such figures appear in secondary sources (e.g., a third-party "estimated earnings" figure), they are noted as unverified context only and excluded from scoring. Each niche was then scored on 10 criteria (0-10, higher = better), with every score's basis — `OBSERVED`, `ESTIMATED`, `INFERRED`, or `EDITORIAL_OPINION` — logged individually.

## Findings by niche family

### 1. European geography, borders & curiosities
Real examples: **RealLifeLore** (7.9-9M subscribers) and **Half as Interesting** (weekly since Aug 2017, 5-12 min videos). Strong, proven demand; the dominant incumbents are globally/US-oriented in English, leaving a real gap for a Europe-first, Spanish-language angle. Visual-legal availability is strong — already demonstrated in this project's own Stage 2 research (Wikimedia Commons categories confirmed for Baarle-Hertog, Vaalserberg, etc.). **Total score: 7.4 (rank 1).**

### 2. Infrastructure, engineering & megaprojects
Real examples: **The B1M** (4M subscribers, 32M viewers/month, official weekly Wednesday upload schedule) and **Ultimate Megaprojects**. Strong demand and good European topic supply (Gotthard Base Tunnel, etc. — already researched in Stage 2), but The B1M itself is host-led (Fred Mills on camera), not purely faceless, and technical 3D-render production raises cost/complexity. **Total score: 6.8 (rank 5).**

### 3. Cities, transport & urbanism
Real examples: **Not Just Bikes** (personal, host-narrated) and **City Beautiful** (top video: 5.7M views, on Gary, Indiana). The best-known example in this niche (Not Just Bikes) is built around a European city (Amsterdam) already — the strongest "Europe fit" score of all 8 niches researched. Somewhat less raw demand than geography or history. **Total score: 7.0 (rank 4).**

### 4. History explained visually
Real examples: **Kings and Generals** (4.07M subscribers, 1,919 videos, Jan 2026) and **The Armchair Historian** (2.49M subscribers). Strong demand and good evergreen supply, but this is the **most saturated** niche researched (multiple well-resourced multi-million-subscriber incumbents), and notably, The Armchair Historian — a successful, well-funded channel — announced an **indefinite hiatus in December 2025**, a real signal that production sustainability is a genuine operator-level risk here, not just a topic-supply question. **Total score: 6.3 (rank 6).**

### 5. Science & technology
Real examples: **Kurzgesagt** (large multi-million subscriber channel) and **Animagraffs** (1.7M subscribers, 146M views). Technology is explicitly cited by industry sources as a top-CPM advertiser category, but this niche has the **lowest competition-entry-difficulty score** of all 8 (i.e., the most saturated by well-funded incumbents) and requires the highest-skill original animation to compete credibly. **Total score: 6.2 (rank 7).**

### 6. Everyday economics & curious data
Real examples: **Economics Explained** (2.85M subscribers, 359.3M total views) and **Two Cents** (2.1M subscribers, PBS Digital Studios, host-led). Finance is explicitly cited as the single highest-CPM faceless category by industry sources. Strong synergy with this project's own Stage 2 research: Eurostat data (already used for a real topic) is openly licensed and directly reusable for this niche. **Total score: 7.1 (rank 3).**

### 7. Kids/family education (Made for Kids)
Real examples: **Homeschool Pop** and **FreeSchool** (both host-narrated, not faceless; subscriber counts not publicly found in this pass). This niche's monetization is **structurally and officially restricted**: YouTube's own "Made for Kids" policy (verified directly against `support.google.com`) disables personalized ads, comments, Super Chat/Stickers/Thanks, Channel Memberships, end screens, and cards; industry sources report resulting RPM around $1-3 versus $5-15 for general content (an estimate, not an official YouTube figure). Combined with COPPA and the EU's GDPR-K compliance burden, this niche's `originality_feasibility` criterion was left `REQUIRES_MANUAL_REVIEW` pending dedicated legal review. **Total score: 5.8 (rank 8, lowest).**

### 8. Nature & wildlife facts (evidence-selected 8th candidate)
Selected after a broad search for "current faceless niche opportunity" surfaced this category repeatedly (OutlierKit and similar industry sources) as low-competition and low-cost specifically because of abundant available stock footage. Real examples: **Natural World Facts** (active since 2012, "Deep Sea Wonders" series) and **Brave Wilderness/Coyote Peterson** (1.19M subscribers this channel, 22.99M combined; explicitly host-led, not faceless). Important honest caveat surfaced during research: the niche's low cost is partly explained by reliance on **licensed/stock wildlife footage** rather than self-produced material — a genuinely faceless, originally-sourced approach here needs the same per-asset visual-rights discipline as any other niche, not an automatic pass. **Total score: 7.3 (rank 2).**

## Cross-cutting observations

- **Format pattern:** among the 16 real channels researched, several of the most successful in "softer"/lifestyle-adjacent niches (The B1M, Not Just Bikes, Two Cents, Homeschool Pop, Brave Wilderness) actually use an on-camera host or personal narrator, not a purely faceless format — while the more data/fact-driven niches (geography, history, science, economics) skew more purely faceless. This is a real, observed pattern relevant to production planning, not an assumption.
- **Language gap:** every real comparable example found across all 8 niches is English-language. No directly comparable large Spanish-language faceless channel was identified in this research pass for any niche — this is itself a data point (an apparent gap/opportunity) but should be treated as `REQUIRES_MANUAL_REVIEW` rather than proof of low competition, since Spanish-language search wasn't exhaustively covered here.
- **Monetization ceiling for kids' content is real and officially documented**, not assumed — directly confirmed against YouTube's own policy pages.
- **No RPM, revenue, retention, or internal competition metric is presented anywhere in this report or its underlying CSVs as a hard number** — every such figure is either absent (`NOT_PUBLICLY_AVAILABLE`) or explicitly labeled as a third-party estimate.

## Addendum (2026-09-19): deepening pass on the 4 shortlisted niches

Following an audit of the original pass, a second research pass specifically targeted the 4 shortlisted niches (geography, cities/urbanism, economics, nature/wildlife) to close identified evidence gaps. Full per-criterion detail: [`../templates/niche-scoring-matrix.csv`](../templates/niche-scoring-matrix.csv) (rows dated 2026-09-19); per-channel detail: [`../templates/channel-video-registry.csv`](../templates/channel-video-registry.csv).

### Direct YouTube verification attempted, and why it failed

A direct WebFetch of every comparable channel's YouTube "About" page was attempted first, per the audit's request. Every single attempt was redirected to YouTube's cookie-consent wall (`consent.youtube.com`); following the consent redirect through to completion returned only page-footer navigation links, with no channel statistics rendered — YouTube's channel header is client-side-rendered and not present in the fetched HTML in this environment. This is a genuine environment limitation, not a skipped step. As a fallback, Social Blade (a standard, widely-used third-party YouTube-statistics tracker) was attempted and returned HTTP 403 (bot-blocked) for every channel. The best available real verification was therefore dated, cited figures surfaced via web search (HypeAuditor rankings, Wikipedia, and similar aggregators/encyclopedic sources) — weaker than a live YouTube fetch, but stronger than the single-blog citations used in the first pass, and every figure now carries a specific date.

### Metrics newly confirmed or corrected

- RealLifeLore: 7,944,011 subscribers, ranked #1669 worldwide, dated September 2026 (was an imprecise "7.9-9M" blog range).
- Half as Interesting: 2,935,101 subscribers, dated June 2026 (was `NOT_PUBLICLY_AVAILABLE`).
- Not Just Bikes: 1.46 million subscribers, 204 million views (was `NOT_PUBLICLY_AVAILABLE`).
- Economics Explained: 2,884,738 subscribers, dated September 2026 (refined from a prior "2.85M").
- Natural World Facts: over 950,000 subscribers, 110 million views (was `NOT_PUBLICLY_AVAILABLE`).
- Brave Wilderness: 210.8 million views on the main channel and 5.5 billion combined views confirmed in addition to the previously-known subscriber counts.
- City Beautiful and Two Cents: **still not resolved to a current figure** — City Beautiful's subscriber count is inconsistent across sources (350K ~2021-22, 651K Jan 2024, an undated 680K mention) with nothing dated 2025/2026 found; Two Cents' only dated figure remains April 2020 (330K). Both are logged honestly as stale/`NOT_PUBLICLY_AVAILABLE`-for-a-current-figure rather than treated as current.

### OutlierKit corroboration (point 2 of the audit)

OutlierKit's own "About" page was located: it is run by three named individuals (Jose, Ayush Chaturvedi, Aditi Chaturvedi) as a commercial YouTube-growth-tool business that sells a niche-research product — a disclosed commercial incentive to portray many niches as low-competition opportunities. No independent second source could be found to corroborate OutlierKit's specific claims for the nature/wildlife niche (production ease, visual-legal availability, competition, sustainability). Per the audit's rule, all four scores were downgraded or replaced with independently-sourced evidence (see the reproducible competition sample below, and the visual-legal findings). This is the clearest single finding of this pass: a claim from a source with an undisclosed-until-now conflict of interest did not survive independent verification.

### Nature/wildlife visual-legal availability, properly researched (point 3)

Concrete, real, verified sources across the required categories:
- **Public domain:** the U.S. Fish & Wildlife Service National Digital Library (`fws.gov/library`) — most content is confirmed public domain and free to use, though *each individual image's copyright status must be checked*, since the library also hosts contributed images that retain copyright.
- **Creative Commons / public-body material:** Wikimedia Commons and iNaturalist (not independently re-verified in this pass beyond the general Commons pattern already confirmed in Stage 2 for other subjects).
- **Free stock libraries:** Pexels, Pixabay, and Unsplash were checked directly — all three confirmed to allow free commercial use of photos/video without attribution (Pixabay and Unsplash explicitly prohibit compiling their content into a competing stock service, a real restriction worth noting for any bulk-sourcing workflow).
- **Material requiring a paid license:** premium/rare-species footage and professional wildlife cinematography (the kind used by high-production channels) is **not** covered by the free sources above and would require a paid stock license or original filming — this resolves the contradiction flagged in the original pass: legally-free material genuinely exists, but it skews toward common species and general nature/landscape shots, not the premium footage that made the niche look "abundant and free" in the original single-source claim.

### Cities/urbanism open-data check (point 4)

Real, active open-data portals were confirmed for 4 European cities: **Amsterdam** (`data.amsterdam.nl` / `maps.amsterdam.nl`, ~300 datasets), **Barcelona** (Open Data BCN, 450+ datasets, CKAN API), **Berlin** (`daten.berlin.de` plus a dedicated Geoportal for geodata), and **Paris** (`opendata.paris.fr`, ODbL-licensed, includes real-time multimodal traffic-counting data). This directly resolves the prior "not verified per-city" gap for these 4 cities; it does not extend to every European city that might eventually be covered.

### CPM/monetization methodology sources (point 5)

No official, published Google/YouTube rate card exists — confirmed directly: YouTube ad pricing is a real-time auction inside Google Ads with no fixed price by category. Every CPM-by-category figure found (including the original Shortimize citation) is an industry-aggregated benchmark, not an official disclosure. This is now stated explicitly rather than implied: `monetization_feasibility_score` for every niche remains a **feasibility judgment**, and no specific CPM/RPM number is used as a scored fact anywhere in this project — see [`09-niche-scoring-methodology.md`](09-niche-scoring-methodology.md).

### Reproducible competition sample (point 6) — ⚠️ CORRECTED 2026-09-20, see below

**Method (defined before counting):** for each of the 4 shortlisted niches, one web search using a fixed query template ("best `[niche]` YouTube channels list 2026") was run once on 2026-09-19; every distinct, named, identifiably-active channel appearing in the synthesized result set was counted. This is a **bounded proxy for visibility/recognition in curated sources** (blogs, rankings, encyclopedic pages), not a direct YouTube search or a census of every channel in the niche, and individual upload activity in the last 6 months was not verified channel-by-channel — that would require dozens of additional individual channel checks beyond this pass's scope.

**Correction (2026-09-20):** an independent review directly fetched all 4 of the citations below and found that 3 of the 4 pointed to real pages that **did not actually name the claimed channels** — one (Economics) pointed to a Wikipedia biography of an unrelated Canadian YouTuber with no connection to economics or finance at all. The 4th (Nature/wildlife) citation returned a server error on re-fetch and could not be confirmed either way. All 4 were re-verified against genuinely different, directly-fetched real sources. The table below shows the **corrected, verified** results; the original (invalid) claims are struck through for transparency, not deleted:

| Niche | ~~Original claim (2026-09-19, invalid citation)~~ | **Corrected result (2026-09-20, verified citation)** | Verified source |
|---|---|---|---|
| Geography | ~~7 channels, cited to a Wikipedia article about one unrelated channel~~ | **9 channels**: RealLifeLore, Atlas Pro, Wendover Productions, Geography Now, Map Men, Half as Interesting, CGP Grey, GeoWizard, Rainbolt | EarthGuessr blog (directly fetched, confirmed) |
| Cities/urbanism | ~~4 channels, cited to a Wikipedia article about one unrelated channel~~ | **5 channels** (fewest of the 4): CityNerd, Banks Rail, Nandert, City Beautiful, Climate Town | URBANEXUS "Urbanism on YouTube" (directly fetched, confirmed) |
| Economics | ~~10 channels, cited to a Wikipedia biography with **no connection to economics at all**~~ | **7 channels**: Economics Explained, The Economic Times, Jacob Clifford, How Money Works, The Economist, Two Cents, Marginal Revolution University | MiniTool listicle (directly fetched, confirmed) |
| Nature/wildlife | ~~11 channels, cited to a page that returned a server error on re-fetch~~ | **15+ confirmed of a claimed 90** (most of the 4): includes Brave Wilderness and Epic Wildlife, confirmed within the first 15 entries | Feedspot "90 Wildlife YouTubers" (directly fetched, confirmed) |

The corrected, verified evidence still supports the same substantive conclusion as before — nature/wildlife is the most crowded of the 4 and cities/urbanism is the least — but via genuinely different sources and channel lists than the invalid 2026-09-19 citations claimed. See [`decisions/ADR-002-niche-format-shortlist-pending-decision.md`](decisions/ADR-002-niche-format-shortlist-pending-decision.md) for the resulting shortlist changes.

### Spanish-language demand (point 7)

| Niche | Observed demand | Indirect signals | Not available |
|---|---|---|---|
| Geography | Daniel Geohistoria (~235K subs); Memorias de Pez (~2.7M subs, adjacent history/geopolitics/curiosities content) | — | No channel matching the exact geography/borders angle at large scale |
| Economics | **VisualPolitik (~3.47M subscribers)** — the strongest real Spanish-demand signal found in this entire pass | — | — |
| Cities/urbanism | — | Urbanópolis (exists, subscriber count not found); a small (~20K subscriber) channel following a single Madrid infrastructure project | No large Spanish-language urbanism channel found |
| Nature/wildlife | — | Several Spanish-language nature/documentary channels exist (Documentales de Animales, NATURALEZA, Free Documentary Nature Español) but appear to rely on licensed/re-uploaded documentary content rather than original faceless production; none with a confirmed subscriber count in this pass | Original-format Spanish wildlife content specifically |

This meaningfully revises the first pass's blanket claim that "no comparable large Spanish-language channel was found for any niche" — geography-adjacent and especially economics content **do** have large, real Spanish-language audiences; cities/urbanism and nature/wildlife remain genuine gaps or `REQUIRES_MANUAL_REVIEW`.

**Correction (2026-09-20):** the 2026-09-19 pass applied this Spanish-demand evidence asymmetrically — Economics' `europe_international_fit_score` was revised upward to reflect the VisualPolitik finding, but Geography's equivalent finding (Memorias de Pez) was left out of Geography's score entirely. Both niches now receive the identical treatment (one real Spanish-language channel citation, same scoring impact) — see [`../templates/niche-scoring-matrix.csv`](../templates/niche-scoring-matrix.csv) row NLOG-0009.

### Faceless-format audit (point 8)

Re-checked, not assumed, for every channel: **confirmed host-led (not faceless)** — Not Just Bikes, City Beautiful, Two Cents, Brave Wilderness. **Confirmed faceless** — RealLifeLore, Half as Interesting, Economics Explained, Natural World Facts. **`REQUIRES_MANUAL_REVIEW`** (not independently confirmed either way in this pass) — Memorias de Pez, VisualPolitik (both newly added Spanish-language dossiers; VisualPolitik in particular is commonly presenter-driven based on general knowledge of the channel, but this was not independently re-verified against actual video content this pass).

### Net effect on scores and ranking — after the source-verification fix (superseded below by the Infrastructure parity pass)

Immediately after the source-verification fix (before the Infrastructure parity pass described next), the ranking stood at: 1. Geography (7.5), 2. Economics (7.4), 3. Cities/urbanism (7.2), 4. Infrastructure (6.8, unchanged throughout, mechanically promoted into the shortlist), 5. Nature/wildlife (6.6). This promotion was flagged at the time as **not yet a fair comparison** — Infrastructure had never been researched to the same depth as the other 3 shortlisted niches.

### Infrastructure parity pass (2026-09-20)

To resolve the fairness gap above, Infrastructure, engineering & megaprojects was brought through the identical protocol used for Geography, Cities, and Economics: a reproducible competition sample from one real, directly-fetched editorial listicle (explicitly **not** an aggregator/directory dump, unlike the wildlife niche's Feedspot source), direct-verification attempts on its comparable channels, a Spanish-language demand check, and a faceless-format audit.

**Competition sample:** WorthWatch, "Best Engineering YouTube Channels for Infrastructure" (directly fetched and confirmed) names 16 channels, including channels also relevant to the Cities/urbanism niche (Not Just Bikes, City Beautiful, CityNerd, RMTransit). Counting only the 12 squarely on-topic for infrastructure/engineering (The B1M, Real Engineering, The Engineering Mindset, Practical Engineering, The Efficient Engineer, Engineering with Rosie, NS Builders, Railways Explained, Building Beautifully, Tiny House Expedition, Transport Matters, Transport for London), this is the **most crowded of the 4 niches evaluated at parity** — more than Geography's 9, Economics' 7, or Cities' 5.

**Visual-legal availability:** a second real megaproject (Golden Gate Bridge) was checked on Wikimedia Commons independently of the Gotthard Base Tunnel example already confirmed in Stage 2, finding strong CC-licensed coverage (379+76+44+145 files across subcategories) — this corroborates, rather than assumes from one example, that the pattern generalizes.

**Spanish-language demand:** a real, dedicated Spanish-language channel for this exact niche (MegaProyectos España) was found to exist, but its subscriber count could not be verified (the analytics site checked returned a paywalled placeholder, not a real figure) — unlike Geography's and Economics' Spanish-demand evidence, this was **not** used to raise the score, since it cannot be confirmed.

**Faceless-format audit:** The B1M is confirmed host-led (Fred Mills, official site). Ultimate Mega Projects is described in search results as using "a digital documentary host," which is ambiguous — not independently confirmed as genuinely faceless in this pass.

**Net effect: Infrastructure's total_score fell from 6.8 to 6.6** (competition_entry_difficulty_score 5→4, visual_legal_availability_score 7→8, originality_feasibility_score 8→6). This exactly ties Nature & wildlife facts (also 6.6) under equal weights. See [`decisions/ADR-002-niche-format-shortlist-pending-decision.md`](decisions/ADR-002-niche-format-shortlist-pending-decision.md) for the disclosed tie-break rule (revenue-oriented weighting decides) and the resulting shortlist.

### Net effect on scores and ranking — final state after both 2026-09-20 passes

Final ranking (equal weights): 1. Geography (7.5), 2. Economics (7.4), 3. Cities/urbanism (7.2), 4. Nature/wildlife (6.6, retains the slot via tie-break), 5. Infrastructure (6.6, loses the tie-break), 6. History (6.3), 7. Science & technology (6.2), 8. Kids/family (5.8). Under revenue-oriented weights: identical top 3 (Geography and Economics effectively tied for 1st, 7.36 vs 7.38), then Nature/wildlife (6.63) ahead of Infrastructure (6.52) outright — no tie in this scenario.

**No niche has been selected as final.** The 4th shortlist slot is explicitly flagged in ADR-002 as a close, scenario-dependent call between two candidates with different, serious trade-offs (Nature/wildlife: most crowded field of any niche, unsubstantiated original pitch, but a proven faceless format; Infrastructure: cleanest demand/visual-rights story, but the most crowded field once measured and an unproven faceless format) — not a settled ranking.

## Limitations

- 2 real examples per niche is a bounded sample, not an exhaustive market survey — useful for relative comparison, not a substitute for deeper due diligence on any single finalist.
- Several dossier fields (exact publish cadence, typical duration, subscriber counts for smaller channels) came back `NOT_PUBLICLY_AVAILABLE` or `REQUIRES_MANUAL_REVIEW` in this pass — see [`../templates/channel-video-registry.csv`](../templates/channel-video-registry.csv) for exactly which.
- Scoring relies heavily on `EDITORIAL_OPINION`/`INFERRED` judgment for several criteria (production cost, automation capability) since no public source quantifies these directly — this is disclosed, not hidden, per [`09-niche-scoring-methodology.md`](09-niche-scoring-methodology.md).
- This report does not constitute legal advice, particularly regarding the Kids/family niche's COPPA/GDPR-K obligations — see the disclaimer in the root [README.md](../README.md).
