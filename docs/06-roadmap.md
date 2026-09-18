# 06 — Roadmap

This roadmap tracks the planned stages of the full system, mapped to the ten goals defined for the project. Stage 1 is the only stage implemented so far.

| Stage | Goal | Status |
|---|---|---|
| 1 | Register source videos; establish project structure, documentation, rights policy, registries, and an n8n skeleton | **Completed** |
| 2 | Automate rights-gate enforcement in n8n (real routing logic, not just a skeleton) | Planned |
| 3 | Transcribe authorized videos | Planned |
| 4 | Analyze transcripts with AI | Planned |
| 5 | Detect segments with clip potential | Planned |
| 6 | Generate vertical clips via Python + FFmpeg | Planned |
| 7 | Enforce mandatory human review before publishing | Planned |
| 8 | Publish to authorized platforms | Planned |
| 9 | Track metrics and results | Planned |
| 10 | Harden the end-to-end pipeline and finalize portfolio write-up | Planned |

## Guiding principle for every future stage

No stage may weaken or bypass the rights gate established in Stage 1 ([`docs/03-content-rights-policy.md`](03-content-rights-policy.md)). Any new automation must be built to enforce that gate more strictly over time, not to route around it for convenience.
