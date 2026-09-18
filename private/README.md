# Private (local-only)

This folder is for **local use only** and is excluded from version control (see `../.gitignore`), except for this `README.md`.

## Intended contents

- References to real license evidence (e.g., `private/licenses/<asset_id>-*.pdf`) that `visual-asset-registry.csv`'s `evidence_reference` field points to by path, without the file itself ever being committed.
- Local working copies of transcripts, raw video, or other sensitive material used during development.
- Any other content that must never be published in this public portfolio repository.

## Rules

- Nothing in this folder (other than this file) should ever be committed. If `git status` shows a file under `private/` other than `README.md`, do not add it — check `.gitignore` first.
- Do not reference real names, emails, contracts, or personal data even in file names inside this folder if the repository is ever made public — treat this folder as sensitive regardless of git tracking.
