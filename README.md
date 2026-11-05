# richmondpilots.org

Static website for [Richmond Pilots](https://richmondpilots.org), a 501(c)(7) equity-based flying club based at [Linden Airport (KLDJ)](https://www.airnav.com/airport/KLDJ) in NJ. The club has been in continuous operation since 1966 and operates two instrument-capable Cessna 172s.

## Hosting

Currently hosted on AWS S3 + CloudFront, served at the apex domain `richmondpilots.org`.

## Stack

Plain HTML + CSS, Bootstrap 3.3.4 via CDN. No build step — files are served as-is.

- `index.html` — single-page site (welcome, meetings, fees, joining, instruction, contact)
- `css/richmond.css` — site-specific overrides on top of Bootstrap
- `img/` — logo and section imagery (members, planes, camping, sky, etc.)
- `docs/` — member-facing downloads (see below)
- `Avtools/` — standalone pilot tools (e.g. tach split calculator)
- `favicon.ico`, `zoho-domain-verification.html` — kept at the root, where browsers and Zoho expect them

## Member-facing assets (`docs/`)

- `RPC_Membership_Application.pdf` — application form linked from the Joining section
- `WB_5272R.xlsx` — weight & balance sheet for Cessna 172M, N5272R
- `WB_38PD.xlsx` — weight & balance sheet for Cessna 172S, N38PD
- `final.pdf` — bylaws / club document linked from the site

When updating hourly rates or membership fees, edit the Fees section of `index.html` directly.

## Local preview

Open `index.html` in a browser.
