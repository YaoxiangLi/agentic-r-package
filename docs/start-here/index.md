---
layout: default
title: Start Here (60–90 min)
nav_order: 2
has_children: false
---

# Start Here (60–90 min)

One end-to-end loop: **spec → patch → test → document → check**.

## What you’ll do

- Choose one small change (a function, a bug, or a doc fix)
- Ask the agent for a minimal patch + tests
- Run verification locally
- Iterate until `devtools::check()` is clean

## Inputs you need

- Package name + goal of the change (1 sentence)
- File paths + function name(s)
- Current code (only the relevant functions)
- Any errors/logs (minimal)

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

