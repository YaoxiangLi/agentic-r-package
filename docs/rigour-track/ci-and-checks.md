---
layout: default
title: CI + check discipline
parent: Rigour Track
nav_order: 3
---

# CI + check discipline

## Minimum gates

- `devtools::test()`
- `devtools::check()` (ideally on at least Linux + Windows)

## Useful local mirrors of CI

```r
devtools::check(remote = TRUE, manual = TRUE)
```

## Release mindset

- Keep a changelog (even a simple `NEWS.md`)
- Avoid merging if `R CMD check` is not clean (or the NOTE isn’t justified)

