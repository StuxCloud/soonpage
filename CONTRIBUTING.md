<p align="center">
  <img src="https://global.media.stux.cloud/logo.png" height="80" alt="Stux.Cloud Logo">
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

## Versioning and changelog

- The version lives in `VERSION.md` (a bare version string) — bump it on every release, following [Semantic Versioning](https://semver.org/)
- Every release gets a `CHANGELOG.md` entry using `### Added` / `### Changed` / `### Fixed` subsections
- `commit.sh` (bash) and `commit.bat` (Windows) read `VERSION.md` to commit and tag a release — no need to edit them per release

## Before committing

- Open `index.html` in a browser and check it renders correctly
- Check the page at common viewport widths (mobile/tablet/desktop) since it's meant to be responsive
