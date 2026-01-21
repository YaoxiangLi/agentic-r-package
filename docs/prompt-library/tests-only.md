---
layout: default
title: Tests-first / regression test prompt
parent: Prompt Library
nav_order: 3
---

# Tests-first / regression test prompt

## Prompt (copy/paste)

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Write testthat tests (3e).
- Prefer stable assertions (types, values, classes); avoid brittle message snapshots unless necessary.
- Keep the repro minimal.

TASK:
Write a failing regression test for: <bug summary>.

SCOPE:
Files: <tests/testthat/test-*.R>
Functions under test: <fn1, fn2>

REPRO:
<paste minimal code>

EXPECTED:
<paste expected behavior>

DELIVERABLE:
One new/updated test file. Include how to run just these tests.
```

## Commands (copy/paste)

```r
devtools::test(filter = "<substring>")
```

