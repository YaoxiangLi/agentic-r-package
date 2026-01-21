---
layout: default
title: Release discipline (lightweight)
parent: Rigour Track
nav_order: 4
---

# Release discipline (lightweight)

## Checklist

- Version bump in `DESCRIPTION`
- `devtools::document()` clean
- `devtools::test()` clean
- `devtools::check()` clean
- Update `NEWS.md` (or equivalent)

## Prompt (copy/paste)

```text
ROLE:
You are an R package release manager.

TASK:
Propose a release checklist and a minimal set of verification commands for this package.

INPUTS:
<paste DESCRIPTION + any known NOTES>
```

