# Python project template

This repo is the starting point for every new Python project on this account.
It also holds the conventions all repos follow: see [docs/GITHUB_STRUCTURE.md](docs/GITHUB_STRUCTURE.md).

## Start a new project from this template

1. On GitHub, click **Use this template → Create a new repository**.
   (First time only: turn on **Settings → General → Template repository** for this repo.)
2. Name the repo following the naming rules in `docs/GITHUB_STRUCTURE.md`.
3. In the new repo, rename the package:
   - `src/project_name/` → `src/<your_package>/`
   - In `pyproject.toml`: `name`, `description`, and `packages = ["src/<your_package>"]`
   - In `tests/test_smoke.py`: the import
4. Replace this README with one describing the project (template below).

## Local setup

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -e ".[dev]"
pytest
```

## Layout

```
.
├── src/project_name/      # package code (src layout keeps imports honest)
├── tests/                 # pytest tests
├── docs/                  # longer docs, decisions, notes
├── .github/
│   ├── workflows/ci.yml   # lint + test on every push and PR
│   ├── ISSUE_TEMPLATE/    # bug and feature templates
│   ├── pull_request_template.md
│   └── dependabot.yml     # monthly dependency updates
├── .env.example           # copy to .env; .env is git-ignored
└── pyproject.toml         # dependencies, ruff, pytest config
```

---

## README template for new projects

```markdown
# <project-name>

One sentence: what it does and who it's for.

## Quick start
## Usage
## Configuration (env vars from .env.example)
## Development (pip install -e ".[dev]" && pytest)
```
