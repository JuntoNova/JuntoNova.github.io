# Junto Nova — staging (test site)

Test site: https://juntonova.github.io/

This repo is the test copy of juntonova.com. Production lives in the
separate repo JuntoNova/JuntoNov and goes live through Cloudflare Workers
Builds on every push to its `main` branch. Nothing in this repo can deploy
production.

## How it works

- Every push to `main` here publishes the test site through GitHub Pages.
- The test site is hidden from search engines: `robots.txt` disallows all,
  every page carries `<meta name="robots" content="noindex,nofollow">`, and a
  thin STAGING bar sits at the top of each page.
- GitHub Pages ignores `_headers` and `_redirects`, so security headers,
  redirects and the custom 404 behave differently here than on live.
- The portal is cut off from the live portal. On juntonova.github.io it never
  calls portal-api.juntonova.com (API is empty in `assets/portal.js` and the
  page's Content-Security-Policy no longer allows that address). It runs on
  built-in sample data instead: staff view by default, client view at
  `portal.html?preview=client`. Edits stay in that browser tab only, and
  "Sign out" just reloads the sample.

## What is only on the test site (Nov 16, 2026)

The dev copy built for review moved here: Your bottom line on the home page
(what you pay, and what you earn and own), the issues grid for all 11 areas
with its Methodology page, and the portal mock with research privacy controls
and the portal issue grid (`portal-grid.html`), which also shows opposing
ideas. Grid data lives in `data/`. The portal pieces run on sample data only.
None of this is on juntonova.com.

## Workflow

1. Build and check every change here first.
2. Production changes need Andrew's explicit exception. Only then does the
   same change go to JuntoNova/JuntoNov.

## Refreshing from live

Copy JuntoNova/JuntoNov `main` over this repo (keep this README, `.nojekyll`
and `.assetsignore`, skip `wrangler.jsonc`), then add the noindex meta and the
STAGING bar to every page and set `robots.txt` to `Disallow: /`.
Then redo the portal cut-off: in `assets/portal.js` set `API = ""`, make
`previewKind()` return sample data on juntonova.github.io, make `logout()`
reload in preview, and drop portal-api.juntonova.com from `portal.html`'s CSP.
Last refreshed from live: JuntoNov main @ 323bd68 (Nov 16, 2026).
