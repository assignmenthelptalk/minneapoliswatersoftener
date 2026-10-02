# minneapoliswatersoftener

Rank-and-rent local lead-generation site for water softener services in
Minneapolis, MN (`minneapoliswatersoftener.com`). Built with Astro (static
output). Deployed via Vercel on push to `main`.

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
