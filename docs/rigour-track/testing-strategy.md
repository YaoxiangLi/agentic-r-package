---
layout: default
title: Testing strategy (pragmatic)
parent: Rigour Track
nav_order: 2
---

# Testing strategy (pragmatic)

## What to prioritize

- Public API behavior (exported functions)
- Error behavior (classes + key message content)
- Edge cases (empty input, NA, type mismatches)
- Regression tests for every bug you fix

## Patterns

```r
testthat::test_that("...", {
  testthat::expect_equal(...)
  testthat::expect_error(..., class = "rlang_error")
})
```

## Keep tests stable

- Avoid assertions that depend on printing, locale, or session state.
- Prefer small, isolated fixtures over large test data dumps.

