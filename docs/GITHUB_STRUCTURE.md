# GitHub structure and conventions

Rules every repo on this account follows, so projects look the same and are easy to find.

## 1. One repo per project

- A **project** is anything you'd deploy, publish, or describe on its own. It gets its own repo.
- Small one-off scripts don't get a repo each. Put them in a single `scripts` repo, one folder per script.
- Code shared by several projects goes in its own library repo (e.g. `py-common`) and is installed with pip.
  Don't copy-paste it between repos.

## 2. Naming

- Lowercase, hyphen-separated: `stock-tracker`, `pdf-invoice-parser`.
- Name it after what it does, not after a codename.
- Optional prefixes to group things in the repo list:

| Prefix | Use for | Example |
|---|---|---|
| `app-` | Things that run (web apps, bots, services) | `app-budget-dashboard` |
| `lib-` | Reusable packages | `lib-common` |
| `tool-` | CLIs and automation | `tool-photo-renamer` |
| `exp-` | Experiments and learning; fine to abandon | `exp-fastapi-tutorial` |
| `notes-` | Non-code knowledge | `notes-homelab` |

- The Python package name is the repo name with underscores and no prefix:
  `tool-photo-renamer` → `photo_renamer`.

## 3. Visibility

- **Private by default.**
- Make a repo public only when it's worth showing and contains no secrets, personal data, or client work.
  Check the full git history before you flip it, not just the current files.

## 4. Every repo has

- [ ] A README with a one-line description and quick start
- [ ] A **description** and **topics** in the repo's About box (topics: `python`, plus the domain such as `automation`, `finance`, `web`)
- [ ] `.gitignore`, `.env.example`, and no committed secrets
- [ ] CI passing on `main`
- [ ] `pyproject.toml` that lists every dependency

All of this comes free when you start from the template.

## 5. Branches and settings

- `main` is always working. Do work on short-lived branches (`feature/…`, `fix/…`) and merge with a PR,
  even when you're the only person working on the repo, so CI runs before the merge.
- Recommended repo settings (Settings → General / Branches):
  - Default branch: `main`
  - Allow squash merging only; turn on "Automatically delete head branches"
  - Branch protection or ruleset on `main`: require PRs and require the `CI / test` check to pass
  - Turn on Dependabot alerts and secret scanning (Settings → Code security)
- On a free plan, rulesets are **only enforced on public repos**. Private repos still run CI on every
  push and PR; just don't merge until the check is green.

## 5a. Non-Python repos

`python-template` is only for Python. For other kinds of project, create an **empty** repo on GitHub
and choose the matching `.gitignore` from the dropdown:

- **iPhone / iOS apps:** pick the `Swift` `.gitignore`. Create the project in Xcode on a Mac, then connect
  it to the repo: Integrate menu → Clone, or Source Control → New Remote. Keep App Store keys,
  provisioning profiles and `GoogleService-Info.plist`-style config files out of git.
- **JavaScript / TypeScript web front ends:** pick the `Node` `.gitignore`.

Naming, visibility, README, topics and lifecycle rules still apply.

## 6. Lifecycle

- **Active**: normal.
- **Paused**: add the `paused` topic and a line at the top of the README.
- **Done or dead**: **archive** the repo (Settings → Danger Zone). Don't delete it; archived repos are read-only and keep their history.

## 7. Account level

- **Profile README**: create a public repo named exactly after your username with a `README.md`;
  GitHub shows it on your profile page. Pin your best 4–6 public repos.
- **Organization (optional)**: if projects start to cluster (e.g. a business or a group of collaborators),
  create a free GitHub organization for that cluster and transfer those repos into it.
  Personal and experimental work stays on your user account.

## 8. Project inventory

Fill this in as repos are created; it's the map of everything.

| Repo | Prefix/type | Visibility | Status | Description |
|---|---|---|---|---|
| `python-template` | template | public | active | Python project template and conventions |
| `Project1` | web app (Python) | private | planned | Web app. Create from `python-template`. |
| `Project2` | iPhone app (Swift) | private | planned | iOS app. Create empty with the Swift `.gitignore`, then push from Xcode. |
