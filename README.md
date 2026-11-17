# Junto Nova test site

Test site: https://juntonova.github.io/

This repo is the test copy of juntonova.com. Production lives in the separate repo JuntoNova/JuntoNov. Nothing in this repo can deploy production.

- Every push to `main` here publishes the test site through GitHub Pages.
- The test site is hidden from search engines: `robots.txt` disallows all, and every page carries a noindex meta tag.
- GitHub Pages ignores `_headers` and `_redirects`, so headers and redirects behave differently here than on live.
- There is no client portal here. Client login goes to https://juntonova.com/portal.

Build and check every change here first. Production changes go to JuntoNova/JuntoNov only after Andrew approves them.
