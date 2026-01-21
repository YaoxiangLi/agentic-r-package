---
layout: default
title: Engineering standards (non-negotiables)
parent: Rigour Track
nav_order: 0
---

# Engineering standards (non-negotiables)

Agentic development is most useful when it speeds up implementation **without lowering standards**. Use this page as the “quality bar” you keep steady while the agent accelerates.

## 1) Scope discipline

- One work item per iteration (one function or one tight cluster).
- Prefer small diffs; avoid drive-by refactors.
- Write acceptance criteria that are testable.

## 2) Correctness discipline

- Validate inputs early; fail fast with actionable messages.
- Preserve backward compatibility unless explicitly breaking.
- Make behavior deterministic (tests should pass on any machine).

## 3) Testing discipline

- Every bug fix gets a regression test.
- New behavior must be tested on happy path + edge cases.
- Prefer stable assertions (values/classes) over brittle message snapshots.
- Keep tests small and local; avoid heavy fixtures unless they pay for themselves.

## 4) API and UX discipline

- Use explicit namespacing in production code (`pkg::fun`).
- Use `cli::cli_abort()`, `cli::cli_warn()`, `cli::cli_inform()` for user-facing messaging.
- Errors should say: what happened, why, and what to do next.

## 5) Package hygiene discipline

- Keep roxygen docs current; examples should run.
- Treat `devtools::check()` as a gate, not a suggestion.
- Track dependency intent: `Imports` (runtime) vs `Suggests` (tests/vignettes/optional).

## Copy/paste: quality gate commands

```r
devtools::document()
devtools::test()
devtools::check()
```

