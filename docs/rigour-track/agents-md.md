---
layout: default
title: AGENTS.md (project conventions that persist)
parent: Rigour Track
nav_order: 2
---

# AGENTS.md (project conventions that persist)

`AGENTS.md` is a lightweight, repo-local “constitution” for your coding agent. It keeps conventions, constraints, and workflow rules close to the code so you don’t have to restate them every session.

This matters because chat sessions have limits (for example, a ~258k context window). A project-level `AGENTS.md` lets the agent reliably re-load the rules even when the conversation history is truncated or you start a fresh thread.

## How Codex uses `AGENTS.md`

Codex treats `AGENTS.md` as instructions with **directory scope**:

- An `AGENTS.md` applies to the entire directory tree rooted at the folder containing it.
- If there are multiple `AGENTS.md` files, the most specific (deepest) one wins when instructions conflict.
- When the agent edits a file, it should follow the `AGENTS.md` that covers that file’s path.

Practical pattern:

- Put one `AGENTS.md` at the repo root for global rules.
- Add narrower `AGENTS.md` files in subfolders only when needed (e.g., `docs/`, `inst/`, a specific module).

## What to put in `AGENTS.md`

Keep it short and enforceable. Focus on rules that prevent churn and regressions:

- **Scope**: “one function cluster per patch”, “no drive-by refactors”
- **R package conventions**: explicit namespacing, no `library()` in package code
- **Errors/messages**: `cli::cli_abort()` / `cli::cli_warn()` usage
- **Testing**: testthat edition, regression tests for bugs, determinism
- **Docs**: roxygen expectations, `devtools::document()` required
- **Verification**: always end with `devtools::test()` + `devtools::check()`

Avoid:

- Long essays, full style guides, or anything the agent can’t verify
- Rules that conflict with the existing codebase unless you’re willing to update code to match

## Make it modular (without losing the “auto-load” benefit)

If you have many conventions, keep `AGENTS.md` readable by splitting rules into two layers:

1) **Core rules** (always): scope, namespacing, errors, tests, verify commands.
2) **Topic modules** (when relevant): logging/progress, plotting, performance, CI, etc.

To keep the “conventions persist across sessions” benefit, the topic module should still live in an `AGENTS.md` file that covers the files being edited. Two common patterns:

- Keep everything in one root `AGENTS.md` and use clear headings.
- Add narrower `AGENTS.md` files by area (e.g., `R/AGENTS.md` for package code, `tests/AGENTS.md` for tests) so the agent only sees what it needs when touching those files.

## How to start (minimum viable `AGENTS.md`)

Create `AGENTS.md` at the repo root and keep it under ~50–120 lines.

Use the template below and adjust for your package.

## How to maintain it (so conventions carry across sessions)

Treat `AGENTS.md` like code:

- Update it when you make a decision that should affect future patches.
- Keep it stable; prefer adding a rule over repeating it in prompts.
- If rules change, update the file first, then ask for code changes.
- When a session gets long, paste a short handoff summary and rely on `AGENTS.md` for standing rules.

## How to use it in prompts

You usually don’t need to paste `AGENTS.md` into the prompt. Instead:

- Keep your prompt focused on the current task and scope.
- If the agent deviates, say “follow `AGENTS.md`” and restate only the violated rule.

## Template (copy/paste)

```md
# AGENTS.md

## Non-negotiables
- Make minimal, safe changes; avoid broad refactors.
- Use explicit namespacing (pkg::fun); no library()/require() in package code.
- Use cli::cli_abort/cli::cli_warn/cli::cli_inform for user-facing messages.
- Add/modify testthat tests (3e). Every bug fix gets a regression test.
- Update roxygen docs for touched functions; run devtools::document().
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

## Scope rules
- One work item per iteration (one file or one tight function cluster).
- Only touch files listed in SCOPE unless you ask first.

## Testing rules
- Prefer deterministic tests; avoid locale/timezone dependence.
- Prefer stable assertions (values/classes) over brittle message snapshots.

## Review / handoff
- End responses with: what changed, files touched, and exact verification commands.
```

## Example module: logging and progress (copy/paste)

Use this when the package has user-facing output, long-running workflows, parallelism, or progress bars.

```md
# R Package Logging And Progress (Best Practice)

Use this guide when adding or modifying user-facing output, logging, or progress
reporting in this repository.

## Principles
- Keep console output concise and user-controlled.
- Never print from worker processes.
- Prefer structured, consistent messaging utilities.
- Make progress reporting robust in both single-core and multi-core runs.

## Messaging
- Use `cli::cli_inform()` for informational messages.
- Use `cli::cli_warn()` for warnings and `cli::cli_abort()` for errors.
- Gate all informational output behind a `verbose` (or `quiet`) argument.
- Avoid `cat()` or `print()` for user-facing output.
- Use `pkg::fun` namespacing; avoid `library()`/`require()` in package code.

## Progress
- Single-core: use `cli` progress (e.g., `cli::cli_progress_*`) or simple
  `cli::cli_inform()` checkpoints for coarse stages.
- Multi-core:
  - Do not emit progress/messages inside workers.
  - Prefer `progressr` with a parallel backend that supports it (e.g., `future`)
    so progress is aggregated in the main process.
  - If using `mclapply`/`parallel`, report progress per chunk only in the main
    process or write logs to files.

## Logging To Files
- When detailed progress is needed for multi-core tasks, add a `log_file`
  argument and write structured lines (e.g., TSV: timestamp, stage, item, status).
- Logging must not change outputs or performance-critical paths by default.

## Defaults
- Default: `verbose = TRUE` with concise `cli::cli_inform()` messages.
- Provide `verbose = FALSE` or `quiet = TRUE` to silence output.
- For long-running steps, emit a start and finish message; avoid per-item output
  in the console.

## Package Quality
- Add roxygen2 docs for exported functions and keep examples fast.
- Validate inputs with clear, actionable error messages.
- Keep R CMD check-friendly behavior: no hidden globals, no side effects on load,
  deterministic where needed (e.g., set a seed in stochastic examples).
- Avoid unnecessary complexity; document if a change increases complexity.
- Prefer clarity over cleverness; follow repository style.

## Plotting
- Prefer ggplot2.
- Use bold x/y axis titles.
- Include an informative title (what + condition + units).
- Add a caption when assumptions or filters are applied.
- If the package defines a theme helper (e.g., `theme_pkg()`), use it.

## Outputs
- When asked to return file contents, output complete files in fenced code blocks,
  and provide tests in a separate block if requested.

## Edit Boundaries
- If an edit-only mode is specified, modify code only between explicit markers
  (e.g., `# BEGIN EDIT` / `# END EDIT`) and keep other sections byte-identical.
```
