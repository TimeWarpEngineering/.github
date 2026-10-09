# Rewrite org profile README to reflect TimeWarp Engineering today

## Description

The org profile page at https://github.com/TimeWarpEngineering renders
`profile/README.md` from this repo (`TimeWarpEngineering/.github`, origin `hub`).
It is old and stale: a "Hi there 👋" header, a Discord badge, a Twitter badge
(the account is now on X), a third-party github-readme-stats card for the
personal `StevenTCramer` user (not the org), and an `http://` visitor counter
dated 2025-02-04. It says nothing about what TimeWarp Engineering is or ships.

Rewrite it so it is current and accurate: what TimeWarp Engineering is now
(Steven T. Cramer's open source work), the TimeWarp suite, the AI agent fleet,
and Ganda.

## Requirements

- Edit **only** `profile/README.md` in this repo. Do not touch any other
  repo's README or any other repo at all.
- **Research first, from live data, not memory.** Use `gh` against the org:
  - `gh repo list TimeWarpEngineering --limit 200 --json name,description,stargazerCount,isArchived,isPrivate,pushedAt,url`
  - Only list **public, non-archived** repos. Note archived/stale ones are left out.
  - Verify each suite project you mention: description, star count, and that it
    is still live (recent pushes, not archived). Candidates include State, Nuru,
    Architecture, Terminal, Amuru, Ganda, Taratibu, Kiini, Mediator, Flow and
    others. Drop any that are private, archived or dead.
- **Never invent numbers.** Stars and counts come from `gh` output at the time
  of writing. Prefer live shields.io badges (e.g. GitHub stars / NuGet version
  badges) over hard-coded numbers where a number would go stale; if you write
  a number in prose, it must match `gh`.
- Content to cover:
  - Who/what: TimeWarp Engineering = Steven T. Cramer's open source org.
  - The TimeWarp suite: one line per live project with link and what it is
    (taken from the repo description / README), grouped sensibly (e.g. libraries
    vs. tools vs. templates).
  - The AI agent fleet: each repo has its own coding-agent bot working its
    own kanban board.
  - Ganda: the tool that drives the agents. It launches coding agents against
    kanban tasks, runs cross-provider review, CI and repo-audit gates, and
    tracks usage. Verify wording against the `timewarp-ganda` repo README.
  - Links: https://timewarp.software/ and https://timewarp.enterprises/ (also
    usable as source material), Steven's X account, and Discord only if the
    invite still works.
- Remove dead/stale elements: the personal-user stats card, the `http://`
  visitor counter, the "Twitter" branding. Keep anything still valid.
- Do not mention, reference or link any project not public in this org.
  Specifically, do **not** mention Wajenzi or Huru in any way.
- Clean GitHub-flavored markdown that renders well on the org page; no
  marketing fluff, no claims that cannot be backed by a repo or site.

## Checklist

- [ ] Research current org repos with `gh` (descriptions, stars, archived, pushedAt)
- [ ] Read timewarp-ganda README and timewarp.software / timewarp.enterprises for wording
- [ ] Rewrite `profile/README.md` (only file changed besides this kitchen)
- [ ] Every listed repo verified public + live; every number matches `gh`
- [ ] One PR for the change
- [ ] Merge via `ganda pr merge`
- [ ] Do not implement on `master`

## Notes

- Hub task **003** (gitignore `*.journal.json`) is still in to-do. If
  `ganda pr merge` / `worktree gc` refuses because `task-work.journal.json`
  is untracked, do not commit the journal; report it.
- Requested by Steven 2026-10-09 (voice). Steven's rule: all repo work goes
  through ganda tasks, never direct edits.

## Results

## Session

- Created: Grok Bot executor (2026-10-09) on TWE-001
