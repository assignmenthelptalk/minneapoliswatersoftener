# Water Softener CITY_NAME STATE_ABBR — Workspace

## Boilerplate build status (informational — not per-city data)
This section tracks what the *template itself* contains, independent of any
city. Update it when the boilerplate gains or loses a component; do not fill
in per-city data here — that's the rest of this file, below.

| Component | Status |
|---|---|
| Keystatic CMS | ❌ REMOVED — phone-call-based rank-and-rent model, site.config.ts edited directly, see PROVISION.md "CMS — No Keystatic" |
| Output mode | Static (`output: "static"`, `@astrojs/vercel`, zero serverless functions) |
| Full design system (global.css) | ✅ commit 3b6e9cf |
| Layout.astro (utility bar + Services-dropdown nav + minimal footer) | ✅ synced from Henderson structural improvements |
| Homepage (10 sections: hero, services grid, GPG data, 2 alternating image-text, CityMap placeholder, service areas, why-choose-us, FAQ accordion, slim CTA bar) | ✅ synced from Henderson structural improvements |
| New pages: repair, about, contact | ✅ created this pass |
| Product-detail pages: products, whole-home-filtration, reverse-osmosis, resin-bed-replacement, brine-tank-cleaning | ✅ commit ea4dfc3 — standard template pages, not yet reflected in the page-status table below until this pass |
| Brand backlink on every inner page | ✅ this pass |
| QuoteForm.astro | ✅ commit 3b6e9cf, updated to use businessEmail |
| Breadcrumbs.astro | ✅ commit 3b6e9cf |
| LocalSchema.astro | ✅ (unchanged, already matched Henderson) |
| GPGSlider.astro | ✅ commit d084265 |
| GPGSliderMini.astro | ✅ commit d084265 |
| SystemTour.astro | ✅ commit d084265 |
| CLAUDE.md | ✅ (pre-existing, unchanged) |
| BRAND-GUIDE.md | ✅ (pre-existing, unchanged) |
| PROVISION.md (Step 5b added, Keystatic step removed, CMS section added) | ✅ this pass |
| HendersonMap.astro | ❌ city-specific, not copied — use CityMap.astro, build per city (needs real pin coordinates) |
| InstallationProcess.astro | ❌ city-specific — build per city (needs local copy) |
| Testimonials.astro | ❌ city-specific — build per city (needs local placeholder copy) |

**Next action**: Ready for Minneapolis provisioning.

GPGSlider/GPGSliderMini/SystemTour all read city data from `site.config.ts`
automatically (city, gpgLow/gpgHigh, gpgLabel, waterSource, waterAuthority) —
no manual editing needed beyond filling in the config. See PROVISION.md
Step 5b for where to add each one.

## Site identity
- Domain:           DOMAIN_NAME
- City:             CITY_NAME, STATE_ABBR
- GPG:              GPG_LOW-GPG_HIGH (GPG_LABEL)
- Water source:     WATER_SOURCE
- Water authority:  WATER_AUTHORITY
- Primary keyword:  PRIMARY_KEYWORD (SEARCH_VOL vol/mo)
- GitHub repo:      assignmenthelptalk/REPO_NAME
- Vercel project:   REPO_NAME
- Vercel URL:       https://REPO_NAME.vercel.app
- Live domain:      https://DOMAIN_NAME

## Folder structure
- Local-SEO-Toolkit/
    data/BUSINESS_ID/topical-map.md        ← topical map
    data/BUSINESS_ID/briefs/               ← EAV briefs per page
    data/BUSINESS_ID/quality-report-*.json ← quality gate reports
- waterSoftenerProjects/REPO_NAME/
    src/site.config.ts                     ← city config (only file changed per city)
    src/pages/                             ← all page files (no CMS layer)
    dist/                                  ← built static HTML (after npm run build)

## Page status
| Page                   | Written | Score  | Ship-ready |
|------------------------|---------|--------|------------|
| homepage               | 🔄      | 63/100 | ❌          |
| water-quality          | 🔄      | 74/100 | ❌          |
| hard-water             | 🔄      | 69/100 | ❌          |
| installation           | 🔄      | 77/100 | ❌          |
| comparison             | 🔄      | 62/100 | ❌          |
| faq                    | 🔄      | 70/100 | ❌          |
| neighbourhood          | 🔄      | 77/100 | ❌          |
| repair                 | 🔄      | 49/100 | ❌          |
| about                  | ✅      | —      | n/a (not EAV-scored) |
| contact                | ✅      | —      | n/a (not EAV-scored) |
| quote                  | 🔄      | 64/100 | ❌          |
| products               | 🔄      | 62/100 | ❌          |
| whole-home-filtration  | 🔄      | 48/100 | ❌          |
| reverse-osmosis        | 🔄      | 57/100 | ❌          |
| resin-bed-replacement  | 🔄      | 58/100 | ❌          |
| brine-tank-cleaning    | 🔄      | 49/100 | ❌          |

16 content pages total (excludes `thank-you`, a form-redirect utility page,
and `[serviceArea]`, a dynamic route populated per QDP-verified service
area — see PROVISION.md Step 5c). 14 of these 16 (all but `about` and
`contact`) are EAV-brief-driven — see Local-SEO-Toolkit's `eavPageTypes.js`.

All 14 scored pages exist as fully dynamic Astro templates (every fact reads
live from `site.config.ts` via `../lib/site`) — there was never a "write from
scratch" step the way older PROMPTS.md language implied. The real Step 5 work
is bringing the shared template prose up to the quality gate's ~40 Koray
rules. First scoring pass (2026-09-22, before any content edits): 57/100
average, 0/14 ship-ready. After one fix pass targeting the rules that
recurred across nearly every page (anchor text exactly matching destination
titles — no trailing arrows, Rule 13/27; an authority-signal + next-step
closer sentence on H2 sections, Rule 21/35; list intro sentences, Rule 26;
one date/currency signal per page, Rule 33/38; H1 title/meta alignment,
Rule 28): 63/100 average, still 0/14 ship-ready. Numbers above are current
as of that second pass.

Update this table after every write and score session.
✅ = done | 🔄 = in progress | ⏳ = not started | ❌ = blocked

## Quality gate (last run: 2026-09-22)
Score threshold: 80/100
Run: cd C:\Users\lenevo\Local-SEO-Toolkit
     npm run score-built-site -- --business BUSINESS_ID --dist [site-path]\dist

## Current task
Keystatic removed, Henderson structural improvements synced (utility bar,
Services-dropdown nav, minimal single-row footer, 10-section homepage,
repair/about/contact pages, brand backlinks on every inner page), static
output confirmed via a clean build (0 errors/warnings, 13 pages, dist/
not dist/client/). Ready for Minneapolis provisioning.

## Local data
- Neighbourhoods:  NEIGHBOURHOOD_1, NEIGHBOURHOOD_2, NEIGHBOURHOOD_3
- ZIP codes:       ZIP_1, ZIP_2, ZIP_3
- County:          COUNTY_NAME
- Population:      POPULATION

## SpringWell affiliate links
- /follow/softener/ — salt-based softener (wired into homepage + comparison)
- /follow/combo/    — softener + filtration combo
- /follow/ro/       — reverse osmosis system

## Provisioning checklist
Mirrors PROVISION.md step-for-step, in the same order — check PROVISION.md
itself if a step here needs more detail than fits on one line.

- [ ] Step 1 — GitHub repo created (`gh repo create`)
- [ ] Step 2 — Boilerplate copied into the repo + `npm install`
- [ ] Step 3 — `src/site.config.ts` filled in with real city data
- [ ] Step 4 — ~~Keystatic~~ REMOVED — no CMS step, see PROVISION.md "CMS — No Keystatic"
- [x] Step 5a — EAV briefs generated (17 files: 13 page types + 4 neighbourhoods) — see Local-SEO-Toolkit\data\minneapoliswatersoftener\briefs\
- [ ] Step 5 — Content written for all 16 pages (see Page status table above)
- [ ] Step 6 — `npm run build` — 0 errors, 0 warnings confirmed
- [ ] Step 6b — All pages scored 80+ via the quality gate
- [ ] Step 7 — Deployed to Vercel (static output, no environment variables needed)
- [ ] Step 8 — Custom domain added (Vercel dashboard + Namecheap DNS)
- [ ] Step 9 — Google Search Console property added, sitemap submitted
- [ ] Step 10 — Citations submitted (Google Business Profile, Yelp, BBB, Angi, HomeAdvisor, Bing Places, Apple Maps, Foursquare, Manta, Hotfrog)

## Notes
_Add any city-specific notes, open data gaps, or decisions made here._

- **2026-09-22 — EAV briefs generated.** Every one of the 17 briefs carries
  the same 8 open data gaps, all installer/business-specific (not
  city-specific): install duration, warranty terms, local equipment+install
  price range, financing plans, local plumbing code/permit requirement, salt
  refill/service interval, grain-capacity sizing guidance, trial/test period.
  These can't be researched — they depend on which real installer/tenant
  signs. Use `[PLACEHOLDER]` for all of them when writing content (per
  PROVISION.md Step 5), and fill them in once a tenant is confirmed.
- **2026-09-22 — searchVol open gap.** No keyword-tool access available to
  verify monthly search volume for "water softener minneapolis mn" —
  `site.config.ts` has `searchVol: 0` as a placeholder. Fill from
  Ahrefs/Semrush/Google Keyword Planner before launch.
- **2026-09-22 — Local-SEO-Toolkit was broken for this boilerplate shape,
  fixed.** `siteConfigAdapter.js`/`tsConfigParser.js` still expected the old
  Keystatic-era `site.config.ts` shape (`phone`/`email`/`formEmail`, a
  `src/data/site.json` file) and couldn't parse the `domain,` shorthand
  property — this broke brief generation, `--register`, and scoring for
  Henderson too, not just this site. Fixed in the toolkit itself (see its own
  git history 2026-09-22); also added `scripts/generate-briefs.js`, which
  didn't exist before, and fixed `score-built-site.js`'s `products` path
  (was hardcoded to Henderson's custom slug).
- **2026-09-22 — accepted quality-gate false positives (do not "fix" these
  by degrading UX or legal copy).** (1) Rule 2/12 flag the standard FTC-style
  affiliate disclosure "We may earn a commission... if you purchase through
  them" for the word "may" and for putting "if" mid-sentence — this is
  correct, expected disclosure language; do not reword it just to satisfy the
  checker. (2) Rules 6/15/20 flag FAQ `<summary>` questions (e.g. "How hard
  is the water in Minneapolis?") as passive/static-verb/context-opening —
  inherent to FAQ format and FAQPage schema, not a real defect. (3) Rule 13/27
  wants breadcrumb anchor text to exactly equal the destination page's full
  SEO title (e.g. "Repair" → "Water Softener Repair and Maintenance in
  Minneapolis") — rejected as a breadcrumb-UX regression; left as the short
  label. (4) Rule 13/27 requires an *exact* string match against
  `eavPageTypes.js`'s `title()` output — a trailing "→" or any other
  character breaks the match. Any future CTA-anchor fix must copy the title
  string with nothing appended.
- **2026-09-22 — quality gate progress, next pass still needed.** First
  fix pass lifted the average from 57→63/100 (0/14 ship-ready both times).
  Remaining recurring failures not yet addressed: Rule 5/7 (breadcrumb +
  brand-backlink intro sentence lacks a concrete example on nearly every
  inner page — likely needs a structural fix, not just prose), Rule 14 (EAV
  triple density — most pages only weave in 1-4 of the 7 real, non-placeholder
  facts from their brief), Rule 41 (repeated sentence openers), Rule 36
  (heading depth layering on repair/brine-tank-cleaning/whole-home-filtration).
  Re-run `node scripts/score-built-site.js --business
  minneapoliswatersoftener --dist ..\minneapoliswatersoftener\dist` from
  Local-SEO-Toolkit after each further pass.
