# Urban Report — policies and support

The privacy policy, terms of service and support page for the Urban Report
iOS app, served by GitHub Pages.

**This repository is public because these documents have to be.** Apple
requires a privacy policy and support URL that a reviewer — and any user —
can open without signing in. Nothing else about the app lives here; the
application source is private.

| Page | URL |
| --- | --- |
| Privacy Policy | `/privacy.html` |
| Terms of Service | `/terms.html` |
| Support | `/support.html` |

Each file is a complete, self-contained HTML document: inline styles, fonts
from Google Fonts, no build step and no shared stylesheet. `.nojekyll` keeps
Pages from running them through Jekyll.

## Changing a document

These are the documents people agree to at sign-up, and acceptance is recorded
against a version number. Anything that changes what a user is agreeing to —
not a typo fix — needs three things to happen together:

1. edit the file here and push, which redeploys Pages;
2. bump the matching entry in `LEGAL_VERSIONS` in the app's
   `apps/mobile/src/lib/legal.ts`;
3. ship a build, so the next acceptance writes a new `consent_records` row.

That table is append-only and keyed on `(user, document, version)`, so a bump
records the new acceptance rather than overwriting the old one. Editing a
document without bumping the version leaves every existing account recorded as
having accepted text that no longer exists — which is exactly the record you
would need if the agreement were ever questioned.

## Do not change these URLs

They are compiled into every released build of the app and submitted to the
App Store. If the documents ever move to their own domain, these paths must
keep resolving — a redirect is fine, a 404 is a broken privacy policy in a
shipped app.
