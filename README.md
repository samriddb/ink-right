# F-1 / J-1 tax residency check

A small static tool that helps F-1 and J-1 students figure out their US tax
residency status (nonresident vs. resident alien) based on public IRS rules —
the first-5-calendar-year exemption for students, the 2-of-6-year exemption
for J-1 scholars, and the substantial presence test once that exemption is
used up.

This is just a calculator. Always confirm your status with
Sprintax, VITA, or your school's international office before filing.

## What it does

- Manual entry of US entry/exit date ranges, or
- Import an I-94 travel history PDF — parsed entirely client-side with
  pdf.js, nothing is ever uploaded anywhere
- Computes your residency status for a chosen tax year, showing the actual
  math (day counts, the substantial presence test formula)
- Tracks your five-year (student) or two-of-six-year (scholar) exemption
  clock

## Running it locally

It's a single self-contained HTML file with one external dependency
(pdf.js, loaded from a CDN at runtime)..

```
open index.html
```

or just double-click it.

## Known simplifications
- The PDF parser matches dates near "arrival"/"departure" language using
  pattern matching, not OCR or AI. Always review the parsed stays before
  trusting the result.
