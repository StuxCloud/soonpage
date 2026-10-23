<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stux.cloud/logo-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stux.cloud/logo-dark.png"><img src="https://global.media.stux.cloud/logo-dark.png" height="80" alt="Stux.Cloud Logo"></picture>
</p>

# Contributing to Coming Soon Page

This is a single-file HTML template, open for use and modification per the
[License](README.md#license) section. This document is for anyone working on
the template itself (not a downstream deployment).

## Local setup

There's no build step or dependencies — just clone the repo and run
`./dev-server.sh [port]` (or `dev-server.bat [port]` on Windows), which starts
a local static server pointed at the directory. Then open
`http://127.0.0.1:8000`.

## Project conventions

- Static HTML pages (`index.html`, `legal.html` + `legal/`, `changelog.html`, `404.html`) — no framework, no build step, no backend.
- Keep it lightweight and dependency-free; fonts are self-hosted under `assets/fonts/` rather than pulled from a third-party CDN — if you add a font weight, update `assets/fonts/fonts.css` and re-check which pages actually reference it.
- `changelog.html` fetches and renders `CHANGELOG.md` at runtime — don't hand-duplicate changelog content into it.
- General contact uses `hello@stux.cloud`; legal-page contact uses `legal@stux.cloud`.
- This page is reused for a service, instance, project, or the website itself — keep copy generic enough to cover all of those.
- Match the existing code style: no comments explaining *what* the markup does, only *why* when something is genuinely non-obvious.
- The sitemap (`sitemap.xml`, `sitemap/index.html`, `robots.txt`) is generated: after adding or removing a page, edit the `PAGES` list in `scripts/build-sitemap.py` and run `python scripts/build-sitemap.py`, then commit the result

## Discord previews and icons

- Every page except `404.html` has a Discord link preview: a pre-built `<script id="discord:component-embed">` block in its `<head>`, written by `python scripts/build-discord-embeds.py` from the page's `<title>` and `<meta name="description">` (the coming-soon page's text and buttons are set at the top of the script; `build-sitemap.py` runs it too). Re-run it after changing a page's title or description or adding a page; `--check` only reports stale pages
- The icon set is `favicon.ico`, `apple-touch-icon.png`, `site.webmanifest` and `assets/img/icon-*.png`. Every page's `<head>` carries the same four tags for them (`favicon.ico`, `icon-512.png`, `apple-touch-icon.png`, `site.webmanifest`); copy them as-is into any new page
- `bash tests/site.sh` (Python 3.8+, no dependencies) checks every preview and the icon set; CI runs it with `tests/version.sh`

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/version.sh` and `bash tests/site.sh`.
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.

## Before committing

- Open `index.html` in a browser and check it renders correctly
- Check the page at common viewport widths (mobile/tablet/desktop) since it's meant to be responsive
