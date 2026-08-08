# Consolidate all CI/CD into a single canonical workflow.yml

## Description

Org convention (timewarp-nuru 458 program; operator ruling 2026-08-08): every
repo has exactly ONE `.github/workflows/workflow.yml` carrying ALL CI/CD
functionality — modes/params are passed in (dispatch inputs, event detection),
never expressed as separate workflow files. **timewarp-nuru is the reference
implementation.** Trusted publishing policies target `workflow.yml` only.

Current workflow files in this repo: sync-configurable-files.md, sync-configurable-files.yml

Disposition: Delete both (abandoned parent sync mechanism). NOTE: this repo later becomes the org's reusable-workflow host (timewarp-ci.yml, 458 Layer 1) — zero workflows is the correct interim state.

## Checklist

- [ ] Exactly one `.github/workflows/workflow.yml` remains carrying all CI/CD (or, for cruft-only repos, zero workflows — do NOT invent CI where none is needed)
- [ ] `sync-configurable-files.*` deleted (abandoned org mechanism)
- [ ] `*.disabled` / `*.bak` cruft deleted
- [ ] Assistant workflows (claude*.yml), if present: explicitly kept (not CI/CD) or folded — record the call here
- [ ] CI still green after consolidation (where CI exists)

## Notes

Created from timewarp-nuru 458-009/458 rollout session, 2026-08-08.

## Results

Both sync-configurable-files.* deleted (abandoned parent sync mechanism).
Zero workflows remain — correct interim state until this repo hosts the org
reusable workflow (458 Layer 1). Duplicate task 002 archived (filing race).

### How to validate

Smoke: `ls .github/workflows/` → empty. Expect: no sync files in repo.
