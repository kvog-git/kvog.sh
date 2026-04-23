# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
hugo server        # Local dev server at http://localhost:1313/
hugo               # Build to ./public/
hugo --minify      # Production build (used by CI)
```

No lint, test, or package install steps — this is a pure Hugo project with no Node dependencies.

## Architecture

This is a Hugo static site (theme: hugo-xmin) deployed to kvog.sh via GitHub Actions on push to `master`. The workflow builds with `hugo --minify` and deploys to GitHub Pages.

- **`hugo.toml`** — site config (baseURL, theme, code highlight style)
- **`content/`** — all Markdown content: `_index.md` (home), `about.md`, `posts/`, `cheatsheets/`
- **`themes/hugo-xmin/`** — minimal theme; layouts and CSS live here
- **`archetypes/default.md`** — template for `hugo new` content
- **`public/`** — build output, not committed (in `.gitignore`)

New content goes in `content/posts/` or `content/cheatsheets/` as Markdown files with Hugo front matter.
