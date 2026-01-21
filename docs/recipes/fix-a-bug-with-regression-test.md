---
layout: default
title: Fix a bug (regression test first)
parent: Recipes
nav_order: 2
---

# Fix a bug (regression test first)

## When to use

- Something used to work and now fails
- You have a concrete repro (inputs + observed output/error)

## Inputs you need

- Minimal repro code (inputs)
- Actual vs expected behavior
- Error/backtrace (if any)
- File + function where the bug likely lives

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Use explicit namespacing (pkg::fun); no library()/require() in package code.
- Use cli::cli_abort/cli::cli_warn/cli::cli_inform.
- Provide full drop-in function definitions (no partial snippets).
- Add/modify testthat tests (3e). Prefer regression tests for bugs.
- Keep changes minimally invasive; no broad refactors unless required.
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

TASK:
Fix bug: <one sentence summary>.

SCOPE:
Files: <R/<file>.R, tests/testthat/test-<topic>.R>
Functions: <fn1, fn2>

ACCEPTANCE CRITERIA:
1) A new test reproduces the bug on current code (fails before fix).
2) After the fix, the test passes and existing tests still pass.
3) Error messages are actionable and use cli::cli_abort() when appropriate.

CURRENT CODE:
<paste relevant functions>

ERRORS/LOGS (minimal):
<paste failing output>
```

## Commands (copy/paste)

```r
devtools::test()
devtools::check()
```

## Definition of Done

- [ ] Regression test exists and is stable
- [ ] Fix is minimal and targeted
- [ ] `devtools::check()` is clean

## Why it works (optional)

Regression tests prevent reintroducing the same failure during future refactors.

