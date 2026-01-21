Paste this and fill placeholders:

```text
ROLE:
You are an expert R package maintainer. Make minimal, safe changes.

CONSTRAINTS:
- Use explicit namespacing (pkg::fun); no library()/require() in package code.
- Use cli::cli_abort/cli::cli_warn/cli::cli_inform.
- Provide full drop-in function definitions (no partial snippets).
- Add/modify testthat tests (3e). Prefer regression tests for bugs.
- Keep changes minimally invasive; no broad refactors unless required.
- End with verification commands: devtools::document(); devtools::test(); devtools::check()

TASK:
<one sentence>

SCOPE:
Files: <R/file.R, tests/testthat/test-file.R>
Functions: <fn1, fn2>

ACCEPTANCE CRITERIA:
1) ...
2) ...
3) ...

CURRENT CODE:
<paste>

ERRORS/LOGS (minimal):
<paste>

DELIVERABLE:
Updated function(s) + updated/added tests + verification commands.
```

