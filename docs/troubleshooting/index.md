---
layout: default
title: Troubleshooting
nav_order: 5
has_children: false
---

# Troubleshooting

Common failure modes + recovery steps.

## `devtools::document()` problems

- `RoxygenNote` changes unexpectedly: update `DESCRIPTION` (let roxygen write it) and commit the change.
- `@export` didn’t export: confirm the roxygen block is directly above the function and re-run `devtools::document()`.
- `@importFrom` not reflected: prefer `pkg::fun` in code; otherwise ensure the roxygen tag is correct.

## Test failures

- Non-deterministic tests: remove randomness or set a seed; avoid relying on locale/timezone.
- Snapshot brittleness: prefer checking classes/values over exact messages unless messages are part of the contract.

## `devtools::check()` / `R CMD check` issues

- `ERROR: dependencies ... are not available`: add missing packages to `Imports`/`Suggests` and use explicit namespacing.
- `Namespace in Imports field not imported from`: either use `pkg::fun` or add a precise `@importFrom`.
- `Non-standard file/directory found at top level`: keep the Jekyll site in `docs/` (not package root) when building a package tarball.
- Windows path issues: normalize paths (`normalizePath(..., winslash = "/", mustWork = FALSE)`), avoid hard-coded drive letters.

## Getting back to a small scope

Paste a handoff summary and restart the thread:

{% include handoff-summary.md %}

