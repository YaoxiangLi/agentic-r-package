---
layout: default
title: Dependencies + namespacing discipline
parent: Rigour Track
nav_order: 1
---

# Dependencies + namespacing discipline

## Defaults

- Prefer `pkg::fun` in package code (clear provenance, fewer NAMESPACE surprises).
- Use `Imports` for runtime dependencies; `Suggests` for tests, vignettes, optional features.
- Avoid broad imports (`@import`) unless there’s a strong reason.

## Quick checks

```r
devtools::check()
```

## Common gotchas

- Using `dplyr`/`rlang`/`purrr` functions without namespacing causes `R CMD check` NOTES/ERRORS.
- Tests can use helpers from `Suggests`, but production code must not.

