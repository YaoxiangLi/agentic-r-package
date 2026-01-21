---
layout: default
title: Start Here (60-90 min)
nav_order: 2
has_children: false
---

# Start Here (60-90 min)

One end-to-end loop: **spec -> patch -> test -> document -> check**.

## What you’ll do

- Choose one small change (a function, a bug, or a doc fix)
- Ask the agent for a minimal patch + tests
- Run verification locally
- Iterate until `devtools::check()` is clean

## Why this loop works

Agentic tooling saves time by generating code and tests quickly, but quality comes from repeating the same engineering loop:

- **Spec**: write acceptance criteria you can test.
- **Patch**: make minimal, safe edits.
- **Test**: prove behavior (including failures) with `testthat`.
- **Document**: keep roxygen and examples aligned with behavior.
- **Check**: trust `devtools::check()` over subjective review.

## Inputs you need

- Package name + goal of the change (1 sentence)
- File paths + function name(s)
- Current code (only the relevant functions)
- Any errors/logs (minimal)
- If the repo is new: a minimal package scaffold + tests (see [Bootstrap a package for agentic work](../recipes/bootstrap-a-package-for-agentic-work/))

## Prompt (copy/paste)

{% include prompt-contract.md %}

## Commands (copy/paste)

```r
# In R
devtools::document()
devtools::test()
devtools::check()
```

```sh
# Optional: run check from shell
R CMD check .
```

## Definition of Done

- New/changed behavior is covered by `testthat` (regression test for bugs)
- Documentation is up to date (`devtools::document()` clean)
- `devtools::test()` passes
- `devtools::check()` passes (or known NOTE is justified and documented)

## Engineering standards (quick checklist)

- **API clarity**: inputs validated; outputs stable; errors actionable (`cli::cli_abort()`).
- **Namespacing discipline**: production code uses `pkg::fun` (avoid `library()` in package code).
- **Test discipline**: add tests for new behavior and every bug fix; keep tests deterministic.
- **Change discipline**: minimal diff; avoid broad refactors unless required by the task.

## If the agent gets “lost”

Use this to reset the thread and re-anchor the scope:

```text
TASK:
<one sentence>

SCOPE:
Files: <...>
Functions: <...>

ACCEPTANCE CRITERIA:
1) ...
2) ...
3) ...
```
