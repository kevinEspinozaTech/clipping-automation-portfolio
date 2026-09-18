# 10 — Niche Selection Process Map (Stage 2B)

Visual summary of how Stage 2B moved from an open question ("which niche/format?") to a provisional shortlist awaiting a human decision. See [`08-market-research-report.md`](08-market-research-report.md) for the full findings and [`09-niche-scoring-methodology.md`](09-niche-scoring-methodology.md) for the scoring rules.

```mermaid
flowchart TD
    A[Define 10 evaluation criteria] --> B[Identify 8 candidate niche families]
    B --> C[Research each niche via public sources]
    C --> D[Log real channel/video evidence\ntemplates/channel-video-registry.csv]
    D --> E[Classify every data point\nOBSERVED / ESTIMATED / INFERRED /\nEDITORIAL_OPINION / NOT_PUBLICLY_AVAILABLE]
    E --> F[Score each niche per criterion\ntemplates/niche-scoring-matrix.csv]
    F --> G[Compute total_score per niche\n= mean of measured criteria]
    G --> H[Rank niches\ntemplates/niche-format-comparison.csv]
    H --> I[Select provisional shortlist\n3-5 top-ranked candidates]
    I --> J[Document advantages / disadvantages /\nrisks per finalist]
    J --> K[Write a reasoned, non-binding\nrecommendation]
    K --> L[docs/decisions/ADR-002\nStatus: Proposed]
    L --> M{{STOP\nHuman decision required}}

    style M fill:#3a3a10,stroke:#f1c40f,color:#fff
    style L fill:#1a2a4a,stroke:#2980b9,color:#fff
```

## What happens after the stop point (not part of this stage)

Only once a human reviews ADR-002 and records a decision does the project resume — either finalizing a niche (updating ADR-002's status and the roadmap) or requesting a deeper look at specific finalists. No script, narration, production, or publishing work begins before that decision, per this stage's explicit scope limit.
