# minneapoliselitewatersoftener

Rank-and-rent local lead-generation site for water softener services in
Minneapolis, MN, under the brand "Minneapolis Elite Water Softener"
(`minneapoliselitewatersoftener.com`). Built with Astro (static output).
Deployed via Vercel on push to `main`.

Renamed 2026-10-07 from minneapoliswatersoftener — folder, domain, and
business name all changed together (same "Elite" brand pattern as
roundrockelitewatersoftener.com). The GitHub repo itself is still named
`minneapoliswatersoftener` pending a manual rename — see WORKSPACE-README.md.

Cloned from [assignmenthelptalk/water-softener-boilerplate](https://github.com/assignmenthelptalk/water-softener-boilerplate) —
see that repo's `PROVISION.md` for how sites like this one get created.

## Content

All city data (water hardness, source, service area, SEO targeting) and
business identity fields (phone, email, address) live in
`src/site.config.ts` — no CMS layer. To update any detail after a tenant
signs, edit the fields directly and `git push`; Vercel rebuilds and
redeploys automatically.

22 pages read from that single config, plus a QDP-gated `[serviceArea]`
dynamic route for nearby cities that have passed the QDP test (see
`PROVISION.md` Step 5c) — Minneapolis already has three service area
entries provisioned (Minnetonka, Plymouth, Bloomington).

## Development

```
npm install
npm run dev      # local dev server
npm run build    # astro check && astro build — must complete with 0 errors, 0 warnings
```
