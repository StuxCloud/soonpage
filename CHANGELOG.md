# Changelog

All notable changes to Soonpage are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/) (MAJOR.MINOR.PATCH).

## v3.0.3

### Changed

- The footer no longer says "Stux.Cloud is operated by Stux Group Ltd."; that belongs on the Imprint, which still says it. The copyright line names Stux.Cloud ("© 2026 Stux.Cloud. All rights reserved.") instead of Stux.Group

## v3.0.2

### Fixed

- The light/dark choice was saved in the browser under `stuxedo-theme`, a name left over from the Stuxedo page this one was built from; it's now `stuxcloud-theme` on every page, and the Cookies Policy names it correctly. A theme picked before this update resets to the system setting once

## v3.0.1

### Changed

- README footer now matches the Stux.Cloud `.github` footer ("Built & Maintained by Stux.Cloud…" and "Stux.Cloud is a part of the Stux.Group brand of businesses"), like every other Stux.Cloud repository

### Fixed

- The imprint said this page is published as Stux.Cloud, "which is operated by Stux.Cloud, which is operated by" Stux Group Ltd, repeating itself; it now reads "published as Stux.Cloud, which is operated by" Stux Group Ltd

## v3.0.0

### Changed

- Rebranded from Stux.Cloud's two-tone green to the single teal `#07878e`, which reads at about 4.1:1 on both the dark and light themes. Every green accent, gradient stop, floating-particle shade and site-banner accent is now `#07878e`; the dark and light backgrounds and text shift from green-tinted to teal-tinted (`#031d1e`, `#e6feff`, `#eef2f2`); button hover is a slightly brighter `#0a9ea6`
- The logo, icon and favicon pick up the new teal Stux.Cloud assets automatically from `global.media.stux.cloud`
- README links the archived earlier designs: [soonpage-v2](https://github.com/StuxCloud/soonpage-v2) (the two-tone green design)

## v1.1.2

### Changed

- The footer's copyright year is worked out automatically: the start year alone in the first year, then START–CURRENT

## v1.1.1

### Changed

- The copyright line reads Stux.Group instead of Stux Group Ltd

### Fixed

- The footer's Created-with icons are optically sized, so the heart no longer looks bigger than the code and coffee icons

## v1.1.0

### Added

- A dev-mode banner, the shared Stux site banner, shown on every page while `dev-server.sh`/`.bat` runs; `?banner=soon,maintenance,site` previews the other banner types locally, and production never shows one (`assets/site-banner.css`, `assets/site-banner.js`, `assets/site-banners.js`, `assets/dev-mode.js`)
- A "Created with love / code / coffee by Stux.Cloud" line in the footer of every page
- `/sitemap` (an HTML page in the site's layout listing every page) and `sitemap.xml`, committed as static files and regenerated with `python scripts/build-sitemap.py` (`lastmod` comes from each page's last git commit); `robots.txt` points at it and the footer links to it

### Changed

- `dev-server.sh`/`.bat` serve the site the way GitHub Pages does (`/changelog` for `changelog.html`, the 404 page for missing paths) through `.github/dev-router.php`, turn DEV_MODE on by default (`--no-dev-mode` to preview production), and run on PHP 7.4 like the other Stux projects (`PHP_BIN`, `php74`, or `%LOCALAPPDATA%\Programs\PHP\7.4`, with a warning otherwise)
- The copyright symbol in the footers is an icon, with a visually hidden "©" so screen readers still read it

## v1.0.4

### Changed
- `changelog.html` now sorts each release's `###` sections into a fixed order — Added, Changed, Fixed, Removed, Security, Deprecated — at render time, rather than trusting the order `CHANGELOG.md` lists them in; unknown section types go last
- Changelog type badges now use the fixed family palette — Added `#2ecc71`, Changed `#3ba7ff`, Fixed `#ffa64d`, Removed `#ff4d4d`, Security `#b06bff`, Deprecated `#8a8a94` — as tinted badges (coloured text on a light tint of the same hue), with darker variants of each for the light theme

## v1.0.3

### Fixed
- The footer's changelog/version link (and other footer links) turned accent-purple once visited — `a:visited` carries a pseudo-class, giving it higher CSS specificity than the plain `footer a` selector meant to keep footer links muted, so it kept winning regardless of source order. Every affected footer link now also styles `footer a:visited` explicitly.

## v1.0.2

### Fixed
- The headline read "This service/instance/project/website is" — an overly long, non-standard variant that also got visually cut off on smaller viewports. Changed to "This service and/or website is", matching the convention already used on StuxAPIs' and Stux.Dev's soonpage/maintenancepage.

## v1.0.1

### Fixed
- GitHub Pages was using the legacy branch-deploy build system, which can silently stop auto-deploying with no error recorded anywhere (discovered on SeasonalOverlaysLibrary — its live site served stale content for over an hour with no visible failure). Switched to GitHub Actions-based Pages deployment (`.github/workflows/pages.yml`), making every deploy an ordinary, observable CI run instead.

## v1.0.0

### Added

- Initial release: self-hosted Exo 2, Barlow and Inter fonts, a "Boring Legal
  Stuff" legal hub (`legal.html` + `legal/`), `changelog.html` that fetches and
  renders `CHANGELOG.md` at runtime, a version indicator fetched live from
  `VERSION.md`, cross-origin `postMessage` title sync, `dev-server.sh` /
  `dev-server.bat`, and a custom `404.html` error page
