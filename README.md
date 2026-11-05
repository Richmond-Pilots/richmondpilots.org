# richmondpilots.org

Static website for [Richmond Pilots](https://richmondpilots.org), a 501(c)(7) equity-based flying club based at [Linden Airport (KLDJ)](https://www.airnav.com/airport/KLDJ) in NJ. The club has been in continuous operation since 1967 and operates two instrument-capable Cessna 172s.

## Hosting

Currently hosted on AWS S3 + CloudFront, served at the apex domain `richmondpilots.org`.

## PR previews

Every pull request from a branch in this repo is deployed to `https://richmondpilots.org/previews/<branch>/` by `.github/workflows/preview.yml`, and a bot comment on the PR links to it. Previews update on each push, are marked `noindex`, and are deleted when the PR closes. The production deploy excludes `previews/*` so it never deletes them.

## Stack

Static site built with [Hugo](https://gohugo.io), a single program with no other dependencies. The version is pinned in both workflow files. GitHub Actions builds the site into `public/` and uploads it.

- `data/club.yaml` — rates, fees, aircraft, meeting details and contact info
- `content/` — pages, in Markdown
- `content/guides/` — guides; add `draft: true` to show a page in previews only
- `layouts/` — page templates, shared header and footer, and the shortcodes used in page content
- `static/` — files served as-is: `css/theme.css`, `img/`, `docs/`, `Avtools/`, `favicon.ico`, `robots.txt` and `zoho-domain-verification.html`

The sitemap is generated automatically and lists Hugo pages only, not files in `static/`.

## Placeholders

Empty values in `data/club.yaml` and `{{</* todo "..." */>}}` in published pages show a highlighted placeholder. The production deploy fails while any published page contains one, leaving the live site unchanged.

## Member-facing assets (`static/docs/`)

- `RPC_Membership_Application.pdf` — application form linked from the Joining section
- `WB_5272R.xlsx` — weight & balance sheet for Cessna 172M, N5272R
- `WB_38PD.xlsx` — weight & balance sheet for Cessna 172S, N38PD
- `final.pdf` — bylaws / club document linked from the site

When updating hourly rates or membership fees, edit `data/club.yaml`, including `rates_effective`. The pages, search descriptions, structured data and "Rates last updated" line all follow from it.

Meeting place changes also go in `data/club.yaml`. The meeting day and time in the structured data are in `layouts/_partials/schema.html`, so update that too if they change. Validate structured data after edits with [Google's Rich Results Test](https://search.google.com/test/rich-results) or the [Schema.org validator](https://validator.schema.org/).

## Local preview

Install Hugo (`brew install hugo` on a Mac), run `hugo server --buildDrafts`, and open the address it prints.
