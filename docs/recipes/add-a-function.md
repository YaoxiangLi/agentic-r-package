---
layout: default
title: Add a function (with tests + docs)
parent: Recipes
nav_order: 1
---

# Add a function (with tests + docs)

## When to use

- You’re adding a new exported or internal helper function
- You want tests + roxygen in the same patch

## Inputs you need

- Function name + whether it’s exported
- File path target (existing `R/*.R` file or new one)
- Expected inputs/outputs (including error cases)
- Any performance constraints

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Use explicit namespacing (pkg::fun); no library()/require() in package code.
- Use cli::cli_abort/cli::cli_warn/cli::cli_inform.
- Provide full drop-in function definitions (no partial snippets).
- Add/modify testthat tests (3e). Include error-case tests.
- Keep changes minimally invasive; no broad refactors unless required.
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

TASK:
Add <pkg>::<fun>() that <does one thing>.

SCOPE:
Files: <R/<file>.R, tests/testthat/test-<fun>.R, man/<fun>.Rd (generated)>
Functions: <fun>

ACCEPTANCE CRITERIA:
1) <fun>(<example>) returns <expected>.
2) Invalid input <case> errors with a clear message via cli::cli_abort().
3) Tests cover happy path + edge cases.

CURRENT CODE:
<paste relevant functions / file skeleton>
```

## Commands (copy/paste)

```r
devtools::document()
devtools::test()
devtools::check()
```

## Definition of Done

- [ ] Function has roxygen (params/return/examples)
- [ ] Tests cover happy path + errors
- [ ] No new NOTES/WARNINGS in `devtools::check()`

## Troubleshooting (optional)

- `Namespace in Imports field not imported from`: ensure roxygen `@importFrom` is correct (or qualify with `pkg::fun`).
- `Rd files out of date`: run `devtools::document()` and re-check.

