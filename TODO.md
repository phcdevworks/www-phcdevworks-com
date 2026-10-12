# PHCDevworks Website Execution Todo

Phase 1 (Foundation) and Phase 2 P0 (Content Depth) were delivered on the
previous implementation — see [ROADMAP.md](ROADMAP.md). The site was rebuilt
on the `@phcdevworks/spectre-init` `astro` starter (2026-10-12); this file
tracks what is still open on the new base.

## Starter Rebuild Follow-Ups

These gaps against the previous setup remain open.

- [ ] Rebuild the site content (homepage, product routes, header, footer,
      metadata) on the starter using `spectre-ui-astro` components and
      shipped `sp-*` classes only, keeping the company-first framing.
- [ ] Decide how `BRAND.md` identity is expressed: stock Spectre theming, or
      a named site brand layer (custom properties only, never `--sp-*`).
      Bradley Potts's call; no site-authored CSS until decided.
- [ ] Restore deployment: choose and add a hosting adapter and deploy script,
      then document it. Deployment stays Bradley Potts's call.
- [ ] Restore a typecheck step in `npm run check` once `@astrojs/check`
      supports TypeScript 7 (currently peers on `^5 || ^6`).
- [ ] Install ESLint and `typescript-eslint` so `eslint.config.ts` is
      enforced, or remove the config.

## Gap: No CI Enforcement of Token/Utility-Only Rule

Confirmed via companywide CSS audit (2026-08-16).
`.github/workflows/ci.yml` runs `npm run check` only, so nothing catches a
regression into raw CSS before merge.

- [ ] Once `project-design/spectre-ui` publishes a raw-CSS/token lint step
      (see that repo's TODO "Gap: No Downstream Enforcement of the Token/
      Utility-Only Rule"), wire it into this repo's `npm run check`/CI.

New website work beyond this opens when a concrete company, ecosystem,
accessibility, performance, or production-readiness need is identified. Keep
additions company-first, scoped to this public website, and grounded in
Spectre packages and patterns before introducing site-specific alternatives.

## Requested by Downstream

None yet.
