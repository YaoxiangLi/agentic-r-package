# Agentic R Package Development (Book)

This repo is a plain-Markdown, copy/paste-first reference for **agentic (Codex-style) R package development** with quality gates (tests, docs, `R CMD check`).

**Site (recommended):** GitHub Pages using Jekyll + Just the Docs.

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
- GitHub repo → **Settings** → **Pages** → **Build and deployment**
  - **Source**: “Deploy from a branch”
  - **Branch**: `main` (or your default) and **Folder**: `/docs`
- After saving, push commits to that branch; Pages rebuilds automatically.

### Base URL (project sites)

If your site URL includes the repo name (`https://<user>.github.io/<repo>/`), set `baseurl` in `docs/_config.yml`:

```yml
baseurl: "/<repo>"
```

For user/org sites (`https://<user>.github.io/`), leave `baseurl` unset.

