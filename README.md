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

## GitHub Pages setup

- Settings → Pages → **Build and deployment**
  - Source: **Deploy from a branch**
  - Branch: `main` (or default) / Folder: `/docs`
