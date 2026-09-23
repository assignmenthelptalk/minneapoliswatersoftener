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

**Next action**: Core provisioning is live (16 fixed pages + 6 expansion
pages + 3 service-area pages, pushed to GitHub, build green). Remaining
work is quality-gate remediation (0/20 pages ship-ready at 80+) and
filling in the real tenant's phone/email once one signs — see Notes.

GPGSlider/GPGSliderMini/SystemTour all read city data from `site.config.ts`
automatically (city, gpgLow/gpgHigh, gpgLabel, waterSource, waterAuthority) —
no manual editing needed beyond filling in the config. See PROVISION.md
Step 5b for where to add each one.

## Site identity
- Domain:           minneapoliswatersoftener.com
- City:             Minneapolis, MN
- GPG:              5-7 (Moderately Hard)
- Water source:     Mississippi River, treated at the Fridley and Columbia Heights plants
- Water authority:  City of Minneapolis Water Treatment & Distribution Services
- Primary keyword:  water softener minneapolis mn (searchVol: 0 — no keyword-tool access this session, still an open gap, see Notes)
- GitHub repo:      assignmenthelptalk/minneapoliswatersoftener (confirmed via `git remote -v`)
- Vercel project:   NOT CONFIRMED this session — no Vercel dashboard access; fill in once verified
- Vercel URL:       NOT CONFIRMED this session
- Live domain:      https://minneapoliswatersoftener.com

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
| Page                            | Written | Score  | Ship-ready |
|----------------------------------|---------|--------|------------|
| homepage                        | 🔄      | 63/100 | ❌          |
| water-quality                   | 🔄      | 74/100 | ❌          |
| hard-water                      | 🔄      | 69/100 | ❌          |
| installation                    | 🔄      | 72/100 | ❌          |
| comparison                      | 🔄      | 62/100 | ❌          |
| faq                             | 🔄      | 70/100 | ❌          |
| neighbourhood                   | 🔄      | 77/100 | ❌          |
| repair                          | 🔄      | 54/100 | ❌          |
| about                           | ✅      | —      | n/a (not EAV-scored) |
| contact                         | ✅      | —      | n/a (not EAV-scored) |
| quote                           | 🔄      | 64/100 | ❌          |
| products                        | 🔄      | 62/100 | ❌          |
| whole-home-filtration           | 🔄      | 48/100 | ❌          |
| reverse-osmosis                 | 🔄      | 57/100 | ❌          |
| resin-bed-replacement           | 🔄      | 58/100 | ❌          |
| brine-tank-cleaning             | 🔄      | 49/100 | ❌          |
| salt-based-installation         | ✅      | 71/100 | ❌          |
| salt-free-installation          | ✅      | 64/100 | ❌          |
| water-softener-sizing           | ✅      | 61/100 | ❌          |
| new-construction-installation   | ✅      | 49/100 | ❌          |
| control-head-repair             | ✅      | 53/100 | ❌          |
| free-water-test                 | ✅      | 57/100 | ❌          |

22 content pages total (excludes `thank-you`, a form-redirect utility page,
and the 3 live service-area pages below, which use the `[serviceArea]`
dynamic route rather than a static file and aren't in this table). 20 of
these 22 (all but `about` and `contact`) are EAV-brief-driven and scored —
see Local-SEO-Toolkit's `eavPageTypes.js`. The 6 new rows (2026-09-23) are
flat top-level pages linked from their parent page (`installation`,
`repair`, or `water-quality`), matching the existing site's URL/component
conventions — not nested under a category folder.

## Service areas (dynamic `[serviceArea]` route, per PROVISION.md Step 5c)
| City       | GPG    | Label       | Data basis | Live |
|------------|--------|-------------|------------|------|
| Minnetonka | 18-20  | Very Hard   | Well count/depth/aquifer confirmed against the 2025 CCR (PWSID 1270031); the GPG itself is a documented **working figure** derived from well depth (444-575 ft) and aquifer geology, since hardness isn't listed in the CCR (unregulated contaminant) | ✅ |
| Plymouth   | 17     | Very Hard   | Well count/depth/aquifer confirmed against the 2025 CCR; GPG confirmed by the site owner directly from Plymouth's official monthly water analysis report (exact document name/date not on file, see verificationSource in site.config.ts) | ✅ |
| Bloomington| 5-6    | Moderately Hard | Fully confirmed against the City of Bloomington's own published Water Quality Report (raw 19 GPG lime-softened to ~5.2 GPG finished, Sam H. Hobbs Water Treatment Plant) | ✅ |

All three built and confirmed live in the sitemap (2026-09-23). **None of
the three are in Local-SEO-Toolkit's `score-built-site.js` `PAGE_MAP`**, so
they are not quality-gate scored — adding them is a separate Local-SEO-Toolkit
task (deliberately not done yet, per instruction). Third-party water-filter/
affiliate sites (Epic Water Filters, Premier Water MN, softprowatersystems)
were checked and explicitly rejected as a data source throughout this
process — see Notes for the full research trail.

Update this table after every write and score session.
✅ = done | 🔄 = in progress | ⏳ = not started | ❌ = blocked

## Quality gate (last run: 2026-09-23)
Score threshold: 80/100. Current: 62/100 average, 0/20 ship-ready
(unchanged from the 2026-09-22 pass — the 6 new pages average close to the
existing pages' quality level, they didn't move the needle either way).
Run: cd C:\Users\lenevo\Local-SEO-Toolkit
     npm run score-built-site -- --business minneapoliswatersoftener --dist [site-path]\dist

## Current task
26 pages built and pushed to GitHub main (`b4be4a0`, 2026-09-23): the
original 16 fixed pages + `thank-you`, 6 new expansion pages
(salt-based-installation, salt-free-installation, water-softener-sizing,
new-construction-installation, control-head-repair, free-water-test), and
3 live service-area pages (Minnetonka, Plymouth, Bloomington). `npm run
build` is clean (0 errors, 0 warnings) and `git push` has been run — Vercel
should auto-deploy per PROVISION.md, not independently re-verified as live
this session. Remaining open items: quality-gate remediation (62/100
average, 0/20 ship-ready), business identity fields (`phoneNumber`,
`businessEmail`, `address` are still literal placeholders pending a
tenant), and wiring the 3 service-area pages into Local-SEO-Toolkit's
`PAGE_MAP` so they get scored too.

## Local data
- Neighbourhoods:  Linden Hills, Longfellow, Powderhorn Park, North Loop
- ZIP codes:       55410, 55406, 55407, 55401
- County:          Hennepin County
- Population:      430,162

## SpringWell affiliate links
- /follow/softener/ — salt-based softener (wired into homepage + comparison)
- /follow/combo/    — softener + filtration combo
- /follow/ro/       — reverse osmosis system

## Provisioning checklist
Mirrors PROVISION.md step-for-step, in the same order — check PROVISION.md
itself if a step here needs more detail than fits on one line.

- [x] Step 1 — GitHub repo created (confirmed via `git remote -v`: assignmenthelptalk/minneapoliswatersoftener)
- [x] Step 2 — Boilerplate copied into the repo + `npm install`
- [x] Step 3 — `src/site.config.ts` filled in with real city data (business identity fields — phone/email/address — remain placeholder pending a tenant, see Notes)
- [ ] Step 4 — ~~Keystatic~~ REMOVED — no CMS step, see PROVISION.md "CMS — No Keystatic"
- [x] Step 5a — EAV briefs generated (17 files: 13 page types + 4 neighbourhoods) — see Local-SEO-Toolkit\data\minneapoliswatersoftener\briefs\ (the 6 new pages and 3 service areas are NOT yet EAV-brief-driven, see Notes)
- [ ] Step 5 — Content written for all pages (see Page status table above — written, but not yet at the 80+ quality bar)
- [x] Step 6 — `npm run build` — 0 errors, 0 warnings confirmed (2026-09-23, 26 pages)
- [ ] Step 6b — All pages scored 80+ via the quality gate (currently 62/100 average, 0/20 ship-ready)
- [x] Step 7 — Pushed to GitHub main, which triggers Vercel auto-deploy per PROVISION.md (live status not independently re-verified this session)
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
- **2026-09-23 — 6 new pages added, following the site's actual flat-URL
  architecture, not a nested `/category/sub-page/` hub layout.** The site
  has no hub pages — `Layout.astro`'s Services/Products nav dropdowns play
  that role instead. New pages: `/salt-based-installation/`,
  `/salt-free-installation/`, `/water-softener-sizing/`,
  `/new-construction-installation/` (all linked from `/installation/`'s new
  "Installation Options" section), `/control-head-repair/` (linked from
  `/repair/`), and `/free-water-test/` (linked from `/water-quality/`).
  None are in the main nav or footer — same precedent as
  `brine-tank-cleaning`, reachable via contextual links + sitemap only.
  Scores: 71/64/61/49/53/57 respectively, none ship-ready. `installation`'s
  own score dropped 77 to 72 from adding the new link section, flagged for
  the next quality-gate pass, not yet fixed.
- **2026-09-23 — 3 service-area pages activated, with three different data
  provenance levels; do not treat them as equally solid.** All three pass
  the Step 5c QDP test (search demand or GBP/Ads evidence, different water
  authority/entity from Minneapolis) and are live in `serviceAreas` with
  `qdp.verified: true`.
  - Bloomington (5-6 GPG, Moderately Hard): fully confirmed against the
    City of Bloomington's own published Water Quality Report, raw well
    water at 19 GPG lime-softened to ~5.2 GPG at the Sam H. Hobbs Water
    Treatment Plant. Corroborated across 5+ bloomingtonmn.gov-hosted PDFs.
    The most solid of the three.
  - Plymouth (17 GPG, Very Hard): water source/authority confirmed against
    the 2025 CCR (17 wells, 302-473 ft, Prairie du Chien-Jordan, Prairie du
    Chien Group, and Jordan aquifers, City of Plymouth Public Works). The
    GPG figure itself is not in the CCR since hardness is unregulated and
    routinely omitted. 17 was given directly by the site owner from
    Plymouth's official monthly water analysis report, but the exact
    document name, date, and URL were never provided. If that citation
    surfaces, add it to `verificationSource` in site.config.ts.
  - Minnetonka (18-20 GPG, Very Hard): water source, authority, well count,
    and well depth confirmed against the Minnetonka 2025 CCR (PWSID
    1270031: 18 wells, 444-575 ft, Prairie Du Chien-Jordan and Jordan
    aquifers, City of Minnetonka Public Works; contact on file: Chuck
    Allan, Utility Superintendent, (952) 988-8427,
    callan@minnetonkamn.gov). The GPG range is explicitly a documented
    working figure, not a CCR-listed number, derived from well depth and
    aquifer geology relative to Plymouth's shallower wells in the same
    formation. This is the most methodologically-derived (least
    directly-measured) of the three GPG figures on this site; replace it
    if an actual lab reading ever surfaces.
  - Rejected as a source throughout, for all three cities: Epic Water
    Filters, Premier Water MN, and softprowatersystems.com. Their numbers
    (Minnetonka 18-20 GPG, Plymouth 22-24 GPG) matched what eventually got
    used or proposed, which is exactly why they were treated with
    suspicion rather than as confirmation. One exchange in this project's
    history involved those exact rejected figures being resubmitted as if
    freshly verified, which did not hold up under a provenance check. Any
    future edit to these three GPG figures should keep citing a real
    document or a named city contact, not a filter-site aggregation.
  - Not done: none of the three are in Local-SEO-Toolkit's
    `score-built-site.js` `PAGE_MAP` yet, so they're unscored. Adding them
    requires a `PAGE_TYPES` entry in `eavPageTypes.js` and a `PAGE_MAP`
    entry, deliberately left as a separate task.
  - Pushed to GitHub main (`fbc9d74` Minnetonka, `b4be4a0` the 6 pages).
    Vercel auto-deploy should follow per PROVISION.md; not independently
    re-verified as live this session.
