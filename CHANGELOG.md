# Changelog

## 0.3.0 — 2026-10-10

- The data cleanup tools were retired on 2026-10-09. Cleaning, labeling, extraction and summaries of
  collected data now go through `everyinfra_chat`, the OpenAI-compatible AI API, free for accounts
  that have topped up, with per-minute limits by cumulative top-up.
- Remove the cleanup transition guide and cleanup examples; update the skill, README files,
  manifests and repository metadata to match.
- Replace the plain-text terminology check in `scripts/validate.py` with a hashed blocklist that also
  covers JSON and YAML files.

## 0.2.0 — 2026-09-06

- Add the EveryData cleanup route (retired in 0.3.0) while preserving `everyinfra_chat` compatibility.
- Document all 15 cleanup operations, entitlement and bounded included-use limits.
- Add inferred field discovery, task listing and original-task recovery by idempotency key.
- Keep activation, submission, partial export, cancellation and deletion as separate decisions.

## 0.1.0 — 2026-09-05

- Standalone packaging for `everyai`.
- Focused English and Chinese README, setup, workflow, examples and repository discovery metadata.
- Imported the reviewed skill and H2 brand assets from the source commit in `repository-metadata.json`.
- Release scope is GitHub source distribution; marketplace approval and live paid-operation tests remain separate.
