---
layout: default
title: Add CI for R CMD check (GitHub Actions)
parent: Recipes
nav_order: 7
---

# Add CI for R CMD check (GitHub Actions)

## When to use

- You want consistent quality gates on every push/PR
- You want failures to be reproducible outside your machine

## Inputs you need

- Target R versions and OS matrix (minimal default: latest release on Linux)
- Whether you need system dependencies (e.g., GDAL, curl, libxml2)

## Prompt (copy/paste)

```text
ROLE:
You are an R package maintainer adding CI with minimal churn.

CONSTRAINTS:
- Prefer r-lib/actions for standard R CMD check workflows.
- Keep the matrix minimal unless requirements demand more.
- Do not change package code unless needed for CI reliability.

TASK:
Add GitHub Actions CI to run R CMD check for this package.

SCOPE:
Files: <.github/workflows/R-CMD-check.yaml, any CI config files>

ACCEPTANCE CRITERIA:
1) CI runs on push + pull_request.
2) CI runs R CMD check and uploads artifacts on failure.
3) Workflow is minimal and standard (r-lib/actions).

CURRENT REPO CONTEXT:
<paste DESCRIPTION + any known system deps>

DELIVERABLE:
Workflow file(s) + short notes on how to adjust matrix/deps.
```

## Commands (copy/paste)

```sh
# Validate YAML quickly (optional)
git status
```

## Definition of Done

- [ ] Workflow exists under `.github/workflows/`
- [ ] Runs on PRs and pushes
- [ ] Shows `R CMD check` results clearly

