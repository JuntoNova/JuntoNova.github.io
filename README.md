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
- The portal page calls the production portal API (portal-api.juntonova.com),
  so signing in or editing ideas on the test site changes real data.

## Workflow

1. Build and check every change here first.
2. Production changes need Andrew's explicit exception. Only then does the
   same change go to JuntoNova/JuntoNov.

## Refreshing from live

Copy JuntoNova/JuntoNov `main` over this repo (keep this README, `.nojekyll`
and `.assetsignore`, skip `wrangler.jsonc`), then add the noindex meta and the
STAGING bar to every page and set `robots.txt` to `Disallow: /`.
Last refreshed from live: JuntoNov main @ 323bd68 (Nov 16, 2026).
