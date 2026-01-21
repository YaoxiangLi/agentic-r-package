---
layout: default
title: Refactor safely (keep behavior)
parent: Recipes
nav_order: 5
---

# Refactor safely (keep behavior)

## When to use

- You need to restructure code without changing externally observable behavior
- You want confidence that you didn’t break edge cases

## Inputs you need

- Target files + functions
- The behavior that must not change (examples + edge cases)
- Any performance constraints (time/memory)

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Preserve behavior (public API + errors) unless explicitly requested.
- Use explicit namespacing (pkg::fun); no library()/require() in package code.
- Use cli::cli_abort/cli::cli_warn/cli::cli_inform for user-facing messages.
- Provide full drop-in function definitions (no partial snippets).
- Strengthen the safety net: add/adjust tests before and/or alongside the refactor.
- Keep refactor scope tight; no unrelated formatting or churn.
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

TASK:
Refactor <fn1, fn2> to <goal: clarity/perf/dup removal> without changing behavior.

SCOPE:
Files: <R/file.R, tests/testthat/test-file.R>
Functions: <fn1, fn2>

BEHAVIOR CONTRACT (must stay true):
1) <example call> returns <expected>.
2) <edge case> returns/errors with <expected>.
3) Error classes/messages remain compatible (don’t remove information).

CURRENT CODE:
<paste relevant functions>

CURRENT TESTS (if any):
<paste relevant tests or say “none”>

DELIVERABLE:
Updated functions + updated/added tests + verification commands.
```

## Commands (copy/paste)

```r
devtools::test()
devtools::check()
```

## Definition of Done

- [ ] Tests cover the behavior contract (including edge cases)
- [ ] Refactor is minimal and readable
- [ ] `devtools::check()` clean

