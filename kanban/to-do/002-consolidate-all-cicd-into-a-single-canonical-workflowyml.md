# Consolidate all CI/CD into a single canonical workflow.yml

## Description

Org convention (timewarp-nuru 458 program; operator ruling 2026-08-08): every
repo has exactly ONE `.github/workflows/workflow.yml` carrying ALL CI/CD
functionality — modes/params passed in. **timewarp-nuru is the reference
implementation.** Trusted publishing policies target `workflow.yml` only.

Current workflow files in this repo: sync-configurable-files.md, sync-configurable-files.yml

Disposition: Delete both (abandoned parent sync mechanism). NOTE: this repo (.github) later becomes the org reusable-workflow host (timewarp-ci.yml, 458 Layer 1) — zero workflows is the correct interim state.

## Checklist

- [ ] Exactly one `.github/workflows/workflow.yml` remains carrying all CI/CD (or zero workflows for cruft-only repos — do NOT invent CI)
- [ ] `sync-configurable-files.*` deleted (abandoned org mechanism)
- [ ] CI still green after consolidation (where CI exists)

## Notes

Created from timewarp-nuru 458-009/458 rollout session, 2026-08-08.
