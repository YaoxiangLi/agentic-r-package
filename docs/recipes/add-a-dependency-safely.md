---
layout: default
title: Add a dependency safely (Imports vs Suggests)
parent: Recipes
nav_order: 6
---

# Add a dependency safely (Imports vs Suggests)

## When to use

- You want to use a new package in production code or tests
- `R CMD check` complains about missing imports / undefined globals

## Inputs you need

- Which package you want to use and which functions
- Where it’s used (production code vs tests vs vignettes)
- Whether the dependency is optional

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Prefer explicit namespacing (pkg::fun) over broad imports.
- Production code must not rely on Suggests-only packages.
- Avoid library()/require() in package code.
- Provide exact edits for DESCRIPTION and any roxygen changes needed.
- Add/modify tests as needed to cover the change.
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

TASK:
Add dependency <pkg> and use <pkg::fun> in <fn>.

SCOPE:
Files: <DESCRIPTION, R/file.R, tests/testthat/test-file.R>
Functions: <fn>

ACCEPTANCE CRITERIA:
1) Dependency is in the correct field (Imports vs Suggests).
2) Package code uses <pkg::fun> (no unqualified calls).
3) `devtools::check()` is clean.

CURRENT CODE:
<paste relevant functions/tests + DESCRIPTION snippets>

DELIVERABLE:
Updated DESCRIPTION + updated code/tests + verification commands.
```

## Commands (copy/paste)

```r
devtools::document()
devtools::test()
devtools::check()
```

## Definition of Done

- [ ] Correct `DESCRIPTION` fields updated
- [ ] Calls are explicitly namespaced
- [ ] `devtools::check()` clean

