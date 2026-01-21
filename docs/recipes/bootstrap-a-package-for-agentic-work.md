---
layout: default
title: Bootstrap a package for agentic work
parent: Recipes
nav_order: 0
---

# Bootstrap a package for agentic work

## When to use

- You’re starting a new package (or an old one lacks tests/docs structure)
- You want a baseline that makes future agent-assisted changes safe and fast

## Inputs you need

- Package name
- Intended license (MIT, Apache-2.0, etc.)
- Whether the package is internal-only or public

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Prefer standard usethis/devtools workflows.
- Avoid unnecessary files; keep the baseline minimal but complete.
- End with verification commands.

TASK:
Bootstrap this repo into a clean R package development baseline for fast, safe iteration.

SCOPE:
Files: <DESCRIPTION, NAMESPACE, R/*, tests/*, README*, LICENSE*>

ACCEPTANCE CRITERIA:
1) testthat (3e) is set up and a sample test runs.
2) Roxygen workflow is enabled; `devtools::document()` runs clean.
3) `devtools::check()` runs clean (or any NOTE is explained).
4) Add a short `AGENTS.md` with project rules (scope, namespacing, errors, tests). Use the template from `docs/rigour-track/agents-md.md`.

CURRENT STATE:
<paste current tree or say “empty repo”>

DELIVERABLE:
Exact file edits + verification commands.
```

## Commands (copy/paste)

```r
# If creating a new package in an empty folder:
usethis::create_package(".")

# Baseline tooling:
usethis::use_testthat(edition = 3)
usethis::use_roxygen_md()
usethis::use_package_doc()

# Verify:
devtools::document()
devtools::test()
devtools::check()
```

## Definition of Done

- [ ] Tests run locally with `devtools::test()`
- [ ] Docs generate with `devtools::document()`
- [ ] `devtools::check()` is clean (or justified NOTE documented)
- [ ] Project rules exist and are easy to follow (`AGENTS.md` / `CONTRIBUTING.md`)
