---
layout: default
title: Spec → patch prompt
parent: Prompt Library
nav_order: 2
---

# Spec → patch prompt

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

TASK:
<one sentence>

SCOPE:
Files: <R/file.R, tests/testthat/test-file.R>
Functions: <fn1, fn2>

ACCEPTANCE CRITERIA:
1) ...
2) ...

CURRENT CODE:
<paste>

DELIVERABLE:
Provide the patch (full function definitions + tests). Then list verification commands.
```

