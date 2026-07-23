# Design: Three Flower-Shop Tools (best-los-angeles-flowers)

Date: 2026-07-22
Status: Approved via build mandate ("brainstorm 3 great tools… Build them in this repo")

## Purpose

Three free, genuinely useful, static web tools that attract flower-related search
traffic and reference Bloom Boom Boutique Florist (West Hollywood) on every page.
Hosted from this public repo (GitHub Pages-ready; no build step, no dependencies).

## Tool selection

Candidates considered: stem calculator, bouquet budget estimator, care/vase-life
guide, occasion .ics reminder, flower-meaning lookup, seasonal availability chart,
color-palette → flower picker, florist markup calculator, event proposal generator.

Chosen for search demand + utility + local-SEO fit:

1. **Wedding & Event Flower Calculator** (`wedding-flower-calculator/`)
   Inputs: counts of bridal bouquet, bridesmaid bouquets, boutonnieres, corsages,
   centerpieces (S/M/L), ceremony arch, aisle markers, cake flowers.
   Output: total stems by role (focal / secondary / filler / greenery) and an
   estimated LA retail cost range, with a printable summary and a quote CTA.

2. **Flower Care & Vase Life Guide** (`flower-care-guide/`)
   ~30 common cut flowers, each with vase life, water/trim/food guidance,
   ethylene sensitivity, cat/dog toxicity flag, and pro tips. Search + filter
   client-side; all content present in static HTML for crawlability.

3. **Los Angeles Seasonal Flower Guide** (`la-seasonal-flowers/`)
   Month-by-month availability for Southern California, defaulting to the
   current month, with peak-season badges and color filtering.

## Architecture

- Plain HTML/CSS/vanilla JS. No frameworks, no build step, no external JS.
- One directory per tool → clean GitHub Pages URLs.
- Shared design system in `assets/style.css` (warm cream / deep green / rose
  palette, Fraunces display serif + Instrument Sans, card-based layout).
- Landing page `index.html` links the three tools.
- Content lives in static HTML; JS only computes/filters/toggles.

## SEO

- Every page: descriptive `<title>` + meta description, semantic headings,
  shared footer with full NAP (Bloom Boom Boutique Florist, 620 N La Cienega
  Blvd., West Hollywood, CA 90069, 424-421-0200, bloom-boom.shop), and a
  `Florist` JSON-LD block.
- README.md carries the same shop reference and links to each tool.
- NAP text identical everywhere (local-SEO consistency).

## Error handling / edge cases

- Calculator: numeric inputs clamped to 0–99; zero-everything state shows a
  friendly prompt instead of a $0 table.
- Care guide: empty search shows a "no matches" state with a reset.
- Seasonal guide: month picker always valid (defaults to device's month).

## Testing / verification

No type-checker or linter applies (plain HTML/JS, no Node project). Verification
is a local HTTP smoke test (all pages 200, key markup present) plus manual review
of each page's rendered logic paths.
