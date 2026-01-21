---
layout: default
title: Update roxygen + NAMESPACE safely
parent: Recipes
nav_order: 4
---

# Update roxygen + NAMESPACE safely

## When to use

- You added/changed functions and need docs/NAMESPACE to match
- You hit `R CMD check` notes about exports/imports

## Inputs you need

- Target function(s) and desired export status
- Dependencies used inside the function(s)
- Current roxygen blocks (if any)

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Use explicit namespacing (pkg::fun); no library()/require() in package code.
- Prefer pkg::fun over broad imports; use @importFrom only when it improves clarity.
- Provide full drop-in roxygen blocks for touched functions.
- Add/modify tests when behavior changes.
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

TASK:
Bring roxygen + NAMESPACE into sync for <fn1, fn2>.

SCOPE:
Files: <R/<file>.R, NAMESPACE (generated), man/*.Rd (generated)>
Functions: <fn1, fn2>

ACCEPTANCE CRITERIA:
1) `devtools::document()` produces no unexpected diffs beyond the intended exports/imports.
2) `devtools::check()` is clean.

CURRENT CODE:
<paste relevant roxygen blocks + functions>
```

## Commands (copy/paste)

```r
devtools::document()
devtools::check()
```

## Definition of Done

- [ ] `NAMESPACE` matches intended exports
- [ ] Rd files updated
- [ ] `devtools::check()` clean

