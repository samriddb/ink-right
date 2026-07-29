# F-1 / J-1 tax residency check

A small static tool that helps F-1 and J-1 students figure out their US tax
residency status (nonresident vs. resident alien) based on public IRS rules —
the first-5-calendar-year exemption for students, the 2-of-6-year exemption
for J-1 scholars, and the substantial presence test once that exemption is
used up.

This is a calculator, not tax advice. Always confirm your status with
Sprintax, VITA, or your school's international office before filing.

## What it does

- Manual entry of US entry/exit date ranges, or
- Import an I-94 travel history PDF — parsed entirely client-side with
  pdf.js, nothing is ever uploaded anywhere
- Computes your residency status for a chosen tax year, showing the actual
  math (day counts, the substantial presence test formula) rather than just
  a bare answer
- Tracks your five-year (student) or two-of-six-year (scholar) exemption
  clock

## Running it locally

It's a single self-contained HTML file with one external dependency
(pdf.js, loaded from a CDN at runtime). No build step, no server.

```
open index.html
```

or just double-click it.

## Deploying

Since it's fully static, any static host works.

**Netlify (fastest):**
1. Drag `index.html` onto [app.netlify.com/drop](https://app.netlify.com/drop)
2. You'll get a live `*.netlify.app` URL immediately

**Custom domain (e.g. via Porkbun):**
1. In your Netlify site → Domain management → Add a custom domain
2. In Porkbun's DNS editor for your domain, add:
   - `ALIAS` record, host blank/`@`, answer `apex-loadbalancer.netlify.com`
   - `CNAME` record, host `www`, answer `your-site-name.netlify.app`
3. Delete any existing Porkbun parking-page records (pointing at
   `pixie.porkbun.com`) first, or the new records will fail to save
4. DNS usually propagates within a few hours; HTTPS is provisioned
   automatically once it does

**GitHub Pages:** enable Pages on this repo (Settings → Pages → deploy from
`main` branch, root folder) and it'll be live at
`https://<username>.github.io/<repo-name>/`.

## Known simplifications

- The J-1 scholar exemption model is simplified — the real IRS rule has
  additional exceptions (e.g. the "predominantly compliant" test) not
  modeled here.
- The PDF parser matches dates near "arrival"/"departure" language using
  pattern matching, not OCR or AI. Always review the parsed stays before
  trusting the result — it's meant to save typing, not to be authoritative.
