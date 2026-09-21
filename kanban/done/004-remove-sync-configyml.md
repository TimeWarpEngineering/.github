# Remove sync-config.yml

## Description

Stop template sync noise by removing sync-config.yml (and related sync workflow/config copies if present). These files drive "Sync configurable files from parent repository" PRs.

## Requirements

- Delete `.github/sync-config.yml`
- Remove or disable any related sync-configurable-files workflow if present
- Close open sync PRs after merge if appropriate
- Do not reintroduce sync-config

## Checklist

- [x] Find all sync-config copies
- [x] Delete them
- [x] Remove related workflow if any
- [x] Commit
- [x] Verify no new sync PRs
- [x] Close stale sync PRs

## Notes

Created to stop recurring template-sync PRs from an active `.github/sync-config.yml`.

## Results

Only one `sync-config.yml` existed: `.github/sync-config.yml`. Deleted it together with the leftover driver `.github/scripts/sync-configurable-files.ps1` (that script existed only to read the config and stage parent-repo copies). `.github/` is now empty and untracked. Org profile content (`profile/README.md`) is unchanged.

Related GitHub Actions were already removed in task 001 (`4c6cb5b` deleted `.github/workflows/sync-configurable-files.yml` and `.github/workflows/sync-configurable-files.md`). No workflow, config, or script remains that can open new sync PRs from this repo.

At implementation (2026-09-21): **3** stale PRs titled "Sync configurable files from parent repository" (`#1`, `#2`, `#3`) closed as obsolete, each with a comment pointing at this cleanup PR. **3** leftover remote branches `sync-configurable-files-*` remain for the coordinator to delete; they are not part of this change.

### How to validate

```bash
git ls-files '.github/**'
# expect: empty

test ! -e .github/sync-config.yml
test ! -e .github/scripts/sync-configurable-files.ps1
test ! -e .github/workflows/sync-configurable-files.yml

gh pr list --repo TimeWarpEngineering/.github \
  --search 'in:title "Sync configurable files from parent repository"' --state open
# expect: empty (do not match this cleanup PR)
```
