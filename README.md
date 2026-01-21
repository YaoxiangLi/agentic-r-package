# Agentic R Package Development

A one-stop, all-in-one reference for building and maintaining R packages with **fast iteration** and **strong engineering standards**. It's designed to sit next to your editor: short pages, consistent structure, and blocks you can copy into your workflow.

If you use agentic tooling to draft code and tests, this book helps keep the codebase healthy and predictable: behavior is specified, changes are scoped, tests are added, docs are updated, and `devtools::check()` stays green.

**Site (recommended):** GitHub Pages (Jekyll + Just the Docs).

## What's inside

- **Start Here (60-90 min):** one full loop (spec -> patch -> test -> document -> check)
- **Recipes:** one page per task (add a function, fix a bug, refactor safely, add CI, etc.)
- **Prompt Library:** reusable templates for patching, tests, QA/review, and handoffs
- **Troubleshooting:** common failure modes and recovery steps
- **Rigour Track:** deeper standards (dependencies, testing strategy, CI/check discipline)

## Who this is for

- R package maintainers who want higher leverage without compromising quality
- Teams who want consistent standards across contributions
- Anyone who prefers “do this next” reference pages over long-form tutorials

## Local preview

1) Install Ruby + Bundler.
2) From `docs/`:

```sh
bundle install
bundle exec jekyll serve
```

Then open `http://127.0.0.1:4000/`.

## GitHub Pages setup (public OK)

- Important: GitHub will warn that **a private repo can publish a public Pages site**. If Pages is enabled, anything in `docs/` becomes publicly readable.
- GitHub repo -> **Settings** -> **Pages** -> **Build and deployment**
  - **Source**: "Deploy from a branch"
  - **Branch**: `main` (or your default) and **Folder**: `/docs`
- After saving, push commits to that branch; Pages rebuilds automatically.

### Base URL (project sites)

If your site URL includes the repo name (`https://<user>.github.io/<repo>/`), set `baseurl` in `docs/_config.yml`:

```yml
baseurl: "/<repo>"
```

For user/org sites (`https://<user>.github.io/`), leave `baseurl` unset.
