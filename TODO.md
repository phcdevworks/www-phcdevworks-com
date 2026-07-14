# TODO.md

# PHCDevworks Website Execution Todo

This todo list is aligned to the roadmap in `ROADMAP.md`. It is scoped to
site structure, content quality, component foundations, accessibility, and
production readiness.

## Phase 1 - Site Foundation: In Progress

Core structure is in place. The following items are complete.

### P0: Route and Layout Structure

- [x] Astro project with Cloudflare Workers SSR adapter configured
- [x] `Layout.astro` with site header, navigation, and footer
- [x] Homepage with hero, product card grid, and principles section
- [x] Route pages: Spectre Design, Spectre Shell, Spectre WordPress
- [x] Global CSS baseline layered on Spectre tokens

### P1: Validation and Toolchain

- [x] `npm run check` gate wired (build + typecheck)
- [x] `npm run preview` via wrangler for Cloudflare runtime checks
- [x] TypeScript ESLint config present (`eslint.config.ts`)

### P2: Documentation and Agent Coordination

- [x] `AGENTS.md` as shared authority document
- [x] `CLAUDE.md` with Claude-specific implementation workflow
- [x] `CODEX.md` with release-agent responsibilities
- [x] `JULES.md` with bounded maintenance scope
- [x] `COPILOT.md` with support-assistant guardrails
- [x] `BRAND.md` with visual identity rules
- [x] `ROADMAP.md` aligned to this todo
- [x] `TODO.md` phased and aligned to `ROADMAP.md`

---

## Phase 2 - Content and Production Readiness

Active phase. Items below are forward-looking and not yet complete.

### P0: Content Depth

- [ ] Expand Spectre Shell page -- startup sequencing, routing, and signals
  content at the depth of the Spectre Design page
- [ ] Expand Spectre WordPress page -- delivery model, icon support, and
  token-aligned integration copy
- [ ] Audit all page copy for PHCDevworks company-first framing (no
  single-product Spectre-only language)

### P1: Reusable Component Foundation

- [ ] Identify first genuinely repeated layout pattern across pages
- [ ] Extract to `src/components/` when a pattern appears in three or more
  places in the same stable form
- [ ] Document component props inline with the Spectre UI Astro approach

### P2: Accessibility, Metadata, and SEO

- [ ] Audit all pages for keyboard navigation completeness
- [ ] Audit all pages for screen reader label coverage (`aria-label`,
  `aria-describedby`, heading hierarchy)
- [ ] Add Open Graph and Twitter card meta tags to `Layout.astro`
- [ ] Verify `<title>` and `<meta name="description">` are accurate on every
  route
- [ ] Add `robots.txt` (check if Astro sitemap integration handles this)
- [ ] Add sitemap generation if not already wired via `@astrojs/sitemap`
- [ ] Add ESLint Astro plugin (`eslint-plugin-astro` + `astro-eslint-parser`)
  and `npm run lint` script when ready

### P3: Responsive Polish and Performance

- [ ] Review all pages at mobile, tablet, and wide-desktop viewports
- [ ] Fix any layout breaks or overflow at narrow widths
- [ ] Check Cloudflare Workers cold-start latency for SSR routes
- [ ] Evaluate Space Grotesk font load -- add subsetting or `font-display`
  optimization if measurable

---

## Recommended Execution Order

1. Page content depth -- most visible gap while pages are live.
2. Accessibility and metadata -- raise baseline before treating site as
   production-ready.
3. Component extraction -- only after content stabilizes and patterns repeat.
4. Responsive polish and performance -- final pass once full content is in place.

## Explicitly Out of Scope

- Upstream token changes -- owned by `@phcdevworks/spectre-tokens`.
- A parallel design system disconnected from Spectre.
- Blog, CMS integration, or content management.
- Moving this site toward a single-product Spectre identity.

## Requested by Downstream

None yet.
