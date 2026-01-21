---
layout: default
title: Agentic workflow patterns (practical)
parent: Rigour Track
nav_order: 1
---

# Agentic workflow patterns (practical)

This book assumes you use an assistant as a productivity multiplier, not a substitute for engineering standards. These patterns reliably improve output quality and reduce back-and-forth.

## 1) Don’t start from empty

Assistants work best with a real package skeleton and a real test harness.

**Minimum baseline**

- `DESCRIPTION`, `NAMESPACE`, `R/`, `tests/`
- `testthat` wired up
- A single “golden path” test you can run quickly

**Commands (copy/paste)**

```r
# Use in a new package repo
usethis::use_testthat(edition = 3)
usethis::use_roxygen_md()
usethis::use_package_doc()
```

## 2) Give the agent a constitution (project rules)

Write down conventions once so every patch is consistent.

Good places for rules:

- `AGENTS.md` (agent-facing)
- `CONTRIBUTING.md` (human-facing)
- `docs/` (domain and workflow notes)

Rule examples that pay off:

- Namespacing: `pkg::fun` in production code
- Errors: `cli::cli_abort()` with actionable messages
- Tests: regression test for every bug fix
- Scope: minimal diffs, no drive-by refactors

## 3) “Skeleton first” beats “explain everything”

When a change is non-trivial, create a small skeleton for the agent to fill:

- File path(s) you want touched
- Function signatures (inputs/outputs)
- A short checklist of behaviors and edge cases

This prevents unnecessary files, keeps scope tight, and makes review easier.

## 4) Strategic context beats dumping the repo

Instead of pasting everything, provide:

- The function(s) being changed
- The tests that cover them (or the place tests should go)
- The exact error/log snippet
- One example call that demonstrates the desired behavior

If the agent needs more, it can ask for it.

## 5) Documentation is a control surface

Treat docs as part of the workflow, not an afterthought:

- Keep roxygen close to behavior (params/return/errors)
- Put “why” and “how to use” notes in `docs/` where the agent can reference them
- Update docs in the same patch as behavior changes

## Copy/paste: repeatable loop

```text
Plan -> Patch -> Verify

Verify:
- devtools::document()
- devtools::test()
- devtools::check()
```

