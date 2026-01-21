---
layout: default
title: Home
nav_order: 1
---

# Agentic R Package Development

A copy/paste-first “cookbook + prompt library” for building R packages with strict quality gates:

- Use agents to generate useful code fast
- Keep engineering standards as the guardrails
- Prove behavior with `testthat`
- Keep docs current with roxygen
- Use `devtools::check()` as the arbiter

## Use this like a tool

- Do the first loop: Start Here → one end-to-end iteration.
- Then live in Recipes + Prompt Library.
- When things break, jump to Troubleshooting.

## The point (speed *with* standards)

Agents are great at accelerating the “typing” part of engineering: scaffolding functions, writing tests, drafting roxygen, and proposing diffs. But stable, high-quality package code still comes from **engineering discipline**:

- Clear scope (small patches)
- Explicit contracts (inputs/outputs/errors)
- Tests as the arbiter (not vibes)
- Documentation as part of the change
- Checks as the quality gate (`devtools::check()`)

This book is optimized for that: copy/paste blocks first, theory optional.

## Sections

- [Start Here (60–90 min)](start-here/)
- [Recipes](recipes/)
- [Prompt Library](prompt-library/)
- [Troubleshooting](troubleshooting/)
- [Rigour Track](rigour-track/)
