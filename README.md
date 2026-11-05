# richmondpilots.org

Static website for [Richmond Pilots](https://richmondpilots.org), a 501(c)(7) equity-based flying club based at [Linden Airport (KLDJ)](https://www.airnav.com/airport/KLDJ) in NJ. The club has been in continuous operation since 1966 and operates two instrument-capable Cessna 172s.

## Hosting

Currently hosted on AWS S3 + CloudFront, served at the apex domain `richmondpilots.org`.

## PR previews

Every pull request from a branch in this repo is deployed to `https://richmondpilots.org/previews/<branch>/` by `.github/workflows/preview.yml`, and a bot comment on the PR links to it. Previews update on each push, are marked `noindex`, and are deleted when the PR closes. The production deploy excludes `previews/*` so it never deletes them.

## Stack

Plain HTML + CSS, Bootstrap 3.3.4 via CDN. No build step — files are served as-is.

- `index.html` — single-page site (welcome, meetings, fees, joining, instruction, contact)
- `css/richmond.css` — site-specific overrides on top of Bootstrap
- `img/` — logo and section imagery (members, planes, camping, sky, etc.)
- `docs/` — member-facing downloads (see below)
- `Avtools/` — standalone pilot tools (e.g. tach split calculator)
- `favicon.ico`, `zoho-domain-verification.html` — kept at the root, where browsers and Zoho expect them
- `robots.txt`, `sitemap.xml` — crawler rules (search and AI crawlers allowed) and the sitemap; bump `<lastmod>` when content changes

## Member-facing assets (`docs/`)

- `RPC_Membership_Application.pdf` — application form linked from the Joining section
- `WB_5272R.xlsx` — weight & balance sheet for Cessna 172M, N5272R
- `WB_38PD.xlsx` — weight & balance sheet for Cessna 172S, N38PD
- `final.pdf` — bylaws / club document linked from the site

When updating hourly rates or membership fees, edit the Fees section of `index.html` directly. Also update:

- the JSON-LD block in the `<head>` of `index.html` (`makesOffer` prices and `validFrom` date), and the meta/Open Graph descriptions if the rate range changes
- the "Rates last updated" line at the bottom of the page
- `<lastmod>` in `sitemap.xml`

Meeting time/place changes also need the `Event` entry in the JSON-LD updated. Validate the JSON-LD after edits with [Google's Rich Results Test](https://search.google.com/test/rich-results) or the [Schema.org validator](https://validator.schema.org/).

## Local preview

Open `index.html` in a browser.
