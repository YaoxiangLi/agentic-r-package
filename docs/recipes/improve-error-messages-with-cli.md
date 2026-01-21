---
layout: default
title: Improve errors/warnings (cli)
parent: Recipes
nav_order: 3
---

# Improve errors/warnings (cli)

## When to use

- Errors are confusing, inconsistent, or missing context
- You want structured, user-facing messages

## Inputs you need

- Current error/warn messages (exact text)
- Inputs that trigger each message
- What the message should say and include (values, types, paths)

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Use explicit namespacing (pkg::fun); no library()/require() in package code.
- Use cli::cli_abort/cli::cli_warn/cli::cli_inform.
- Provide full drop-in function definitions (no partial snippets).
- Update tests to assert on class/message when stable.
- Keep changes minimally invasive; no broad refactors unless required.
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

TASK:
Standardize errors/warnings in <fn> to be clear and consistent.

SCOPE:
Files: <R/<file>.R, tests/testthat/test-<fn>.R>
Functions: <fn>

ACCEPTANCE CRITERIA:
1) Invalid inputs fail fast with cli::cli_abort() and actionable messages.
2) Warnings use cli::cli_warn() with consistent phrasing.
3) Tests confirm key message content (without being brittle).

CURRENT CODE:
<paste relevant functions>

ERRORS/LOGS (minimal):
<paste current messages>
```

## Commands (copy/paste)

```r
devtools::test()
devtools::check()
```

## Definition of Done

- [ ] Messages use `cli` consistently
- [ ] Tests cover primary invalid-input cases
- [ ] `devtools::check()` clean

