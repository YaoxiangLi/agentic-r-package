---
layout: default
title: QA / review prompt
parent: Prompt Library
nav_order: 4
---

# QA / review prompt

## Prompt (copy/paste)

```text
ROLE:
You are a meticulous R package reviewer.

CONSTRAINTS:
- Focus on correctness, test coverage, user-facing errors, and `R CMD check`.
- Suggest minimal changes; avoid broad refactors.

TASK:
Review this patch for correctness and package-quality risks.

SCOPE:
Files changed: <list>
Functions changed: <list>

PATCH:
<paste diff or updated code>

DELIVERABLE:
1) Findings grouped by severity (must-fix / should-fix / nice-to-have).
2) Concrete edits for must-fix items.
3) Verification commands to re-run.
```

