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

- [x] Research current org repos with `gh` (descriptions, stars, archived, pushedAt)
- [x] Read timewarp-ganda README and timewarp.software / timewarp.enterprises for wording
- [x] Rewrite `profile/README.md` (only file changed besides this kitchen)
- [x] Every listed repo verified public + live; every number matches `gh`
- [ ] One PR for the change
- [ ] Merge via `ganda pr merge`
- [x] Do not implement on `master`

## Notes

- Hub task **003** (gitignore `*.journal.json`) is still in to-do. If
  `ganda pr merge` / `worktree gc` refuses because `task-work.journal.json`
  is untracked, do not commit the journal; report it.
- Requested by Steven 2026-10-09 (voice). Steven's rule: all repo work goes
  through ganda tasks, never direct edits.

## Results

Rewrote `profile/README.md` from the 2026-10-09 `gh repo list` snapshot. The page now says who the org is, lists each public original project that was pushed in 2026, and describes the agent workflow. Star counts and NuGet versions are shields.io badges, so the prose has no hard-coded counts.

Included public, non-fork, non-archived repos (name, stars, pushedAt from `gh`):

| Repo | Stars | Pushed |
| --- | ---: | --- |
| timewarp-state | 612 | 2026-10-09 |
| timewarp-nuru | 114 | 2026-10-09 |
| timewarp-architecture | 54 | 2026-10-09 |
| timewarp-simple-icons | 30 | 2026-09-20 |
| timewarp-heroicons | 23 | 2026-09-03 |
| timewarp-amuru | 18 | 2026-10-07 |
| timewarp-mediator | 15 | 2026-10-09 |
| timewarp-fixie | 5 | 2026-09-21 |
| timewarp-source-generators | 4 | 2026-09-20 |
| timewarp-build-tasks | 3 | 2026-10-02 |
| timewarp-multiavatar | 3 | 2026-09-03 |
| timewarp-options-validation | 3 | 2026-09-03 |
| timewarp-terminal | 2 | 2026-10-09 |
| timewarp-flexbox | 1 | 2026-09-03 |
| timewarp-jaribu | 1 | 2026-09-22 |
| timewarp-quickbooks | 1 | 2026-10-09 |
| timewarp-builder | 0 | 2026-09-03 |
| timewarp-components | 0 | 2026-09-03 |

One-line descriptions come from the repo description or the README. Empty GitHub descriptions use the README (Terminal, Amuru, Build.Tasks, Builder, Multiavatar, OptionsValidation, Flexbox, SourceGenerators). QuickBooks has no README; the line is the GitHub description, "Quickbooks Online integration". Architecture's GitHub description still says Tye and YARP; the profile uses the README (`dotnet new timewarp-architecture`) instead.

Left out on purpose:

- 60 private or archived repos. Ganda is private. The profile describes it and does not link the repository. No other private repository is named.
- 73 public forks.
- Public originals that are not current: `staruml-export-plantuml` (pushed 2023-04-11), `timewarp-source-code-generators` (2021-11-18), `UI-Layer` (2018-02-24).
- `timewarp-blazor-cli`: `pushedAt` is 2026-05-18, but the default branch commit is 2022-01-23, the README is still a template, and there is no `kanban/` directory.
- `timewarpengineering.github.io`: pushed 2026-09-03 for kanban chores. Its README is a copied State page and links `https://timewarp.ws/`, which returned HTTP 522. The profile uses that repo only for the logo PNG.

Ganda wording follows `timewarp-ganda` `readme.md` and `source/timewarp-ganda/readme.md`. Those files say Ganda launches a coding-agent profile against a kanban task and that `ganda repo audit` is the repo gate. Profiles named there are `implementer-grok`, `implementer-opencode`, and `implementer-cursor`. They do not say Ganda tracks usage, and they do not say Ganda runs CI. "usage pick" in that README is a decision-model confidence column. The profile does not claim usage tracking or a CI gate.

Agent evidence: every listed project has a `kanban/` directory. Org installations include the `claude`, `grok-by-xai`, and `cursor` GitHub apps. Recent commits on State, Nuru, Architecture, Amuru, Mediator, and Terminal include Claude or Grok co-authors. There is no separate bot user per repo; commits are authored by StevenTCramer.

Discord invite `https://discord.gg/97tvbEr2AQ` still resolves (guild TheFreezeTeam, `expires_at` null). The X link is `https://x.com/StevenTCramer`, which matches the org `twitter_username` and timewarp.enterprises. The personal stats card, the Twitter follow badge, and the `http://` visitor counter are gone.

PR open and `ganda pr merge` stay unchecked. Those are later host nodes. This walk did not run `gh pr create`, `ganda kanban done`, or a merge.

The untracked `.gitignore` in the worktree (journal and oracle log patterns) was not committed. That file is hub task 003.

### How to validate

Smoke:

```bash
git diff origin/master -- profile/README.md
rg -i 'wajenzi|huru|twitter\.com|github-readme-stats|estruyf|http://' profile/README.md
```

Expect:

- The diff is the org profile rewrite. The only other product-adjacent edit is this kitchen file.
- The `rg` command prints nothing.
- The rendered page names Steven T. Cramer and links `https://timewarp.software/`, `https://timewarp.enterprises/`, `https://x.com/StevenTCramer`, and the Discord invite above.
- Each project row links a repo in the table in this section. Shields badges show the star count and the NuGet version. The prose does not repeat those numbers.
- Ganda is described and has no GitHub link.

## Session

- Created: Grok Bot executor (2026-10-09) on TWE-001
- Implementation: Grok implementer (2026-10-09) on `task/005-rewrite-org-profile-readme-to-reflect-timewarp-eng`
