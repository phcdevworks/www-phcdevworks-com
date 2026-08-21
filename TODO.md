# PHCDevworks Website Execution Todo

## Active: Reduce Hand-Rolled CSS, Migrate to Spectre Recipes/Utilities

Confirmed via companywide CSS audit (2026-08-16). The last built site CSS
(`dist/client/_astro/Layout.*.css`, captured before `src/styles/global.css`
was emptied for an in-progress rewrite) shows a large per-page hand-authored
CSS layer — `hero-atmosphere`, `home-hero`, `home-product-card*`,
`spec-list__item`, `asset-card__inner`, `site-nav__link`, `site-footer*`,
`install-block`/`code-block`/`code-pill`, `page-intro`, `display-headline`,
`eyebrow` — mixing `var(--sp-*)` tokens with raw magic numbers (`min-height:
44rem`, `filter: blur(64px)`, `border-radius: 9999px`, hardcoded `@media
(width>=768px)` instead of `sp-lg-*`), and the same list/card patterns
reimplemented independently per page (`index.astro`, `spectre-shell.astro`,
`spectre-wordpress.astro`, `spectre-design.astro`) rather than shared. This is
exactly the "custom `<style>` block with raw spacing/layout values" pattern
`project-design/CLAUDE.md`'s one hard rule prohibits.
`docs-phcdevworks-com/src/layouts/DocsLayout.astro` is the model to follow —
it composes `spectre-ui` recipe functions (`getNavLinksClasses`, etc.)
instead of hand-rolling classes.

- [ ] Once the in-progress `src/styles/global.css` rewrite lands, re-audit it
      against this list before doing anything else — it may already resolve
      some of these.
- [ ] Replace hand-rolled list/card layouts (`spec-list` in
      `spectre-shell.astro:50-67`, `asset-list`/`asset-card__inner` in
      `spectre-wordpress.astro:43-61`) with `SpGrid`/`SpCard`/`SpStack` —
      these components are already imported in the same files.
- [ ] Extract the repeated `page-intro`/`eyebrow`/`code-pill`/`install-block`
      patterns into `src/components/` once confirmed shared across 3+ pages,
      built from Spectre recipes rather than page-local classes (this is also
      the trigger already named in `project-web/TODO.md`'s "Not Yet Scoped"
      Phase 2 P1 item).
- [ ] For any layout/spacing/typography property that has no `sp-*` utility
      or recipe today (e.g. the flex `align-content`/`order`/`flex-basis`
      gaps and the display-type weight/tracking gap already tracked in
      `project-design/spectre-ui/TODO.md`), file or confirm the gap there
      instead of leaving the local hand-rolled CSS in place.
- [ ] Add a CI lint step once `project-design/spectre-ui` publishes one (see
      that repo's TODO "Gap: No Downstream Enforcement of the Token/
      Utility-Only Rule") — `.github/workflows/ci.yml` currently only runs
      build + typecheck, nothing catches raw CSS before merge.

New website work beyond this opens when a concrete company, ecosystem,
accessibility, performance, or production-readiness need is identified. Keep
additions company-first, scoped to this public website, and grounded in
Spectre packages and patterns before introducing site-specific alternatives.
