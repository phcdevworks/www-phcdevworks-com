# Changelog

All notable changes to `www-phcdevworks-com` should be documented in this file.

The format follows Keep a Changelog and uses semantic versioning where
practical.

## Unreleased

- Switched site typography to a two-font system: Manrope for headings
  (`font-display`), Inter for body copy (`font-sans`) — replaces the single
  Space Grotesk face.
- Rewrote homepage copy company-first, adding an engineering-principles
  section ahead of the Spectre product grid so the page no longer reads as a
  single-product Spectre page. Flattened the card system to the `flat`
  variant everywhere (was a mix of `outline` and `elevated`, the latter with
  a shadow rule `BRAND.md` calls out to avoid) and dropped the now-unused
  package-pill list styling.
- Rebuilt the footer with `SpFooter`, `SpContainer`, `SpStack`, and `SpText`
  from `spectre-ui-astro` (was hand-rolled markup), reusing the header's real
  nav items instead of dummy links. Restructured to a centered, stacked
  layout — icon brand mark, inline nav list, social icon row, centered
  copyright line — with real links to PHCDevworks' X, GitHub, LinkedIn, and
  Facebook profiles as inline SVG icons. Removed the placeholder hexagon
  glyph next to "PHCDevworks" in the brand mark, since it wasn't the actual
  company logo.
- Fixed a site-wide light-theme regression found while verifying the footer
  rebuild in-browser: `spectre-ui/index.css` sets `:root` custom properties
  unlayered, which beat `global.css`'s `@layer base` override regardless of
  source order. Fixed by setting `data-spectre-theme="dark"` on `<html>`.
- Bumped `astro`, `wrangler`, `@astrojs/cloudflare`, `@astrojs/check`,
  `playwright`, and `@types/node` to their latest published patch/minor
  versions, and approved the `workerd` postinstall script npm's
  install-scripts allowlist blocked after the bump.
- Upgraded Astro from `^6.4.8` to `^7.1.3` and bumped `@phcdevworks/spectre-tokens`
  to `^3.5.0`, `@phcdevworks/spectre-ui` to `^2.10.0`, and
  `@phcdevworks/spectre-ui-astro` to `^3.7.0` (was 2 majors behind on the
  Astro adapter's peer dependency). Bumped `@astrojs/cloudflare` to `^14.1.4`
  and `wrangler` to match.
- Bumped `@phcdevworks/spectre-tokens` to `^4.0.0`, `@phcdevworks/spectre-ui`
  to `^3.1.0`, and `@phcdevworks/spectre-ui-astro` to `^4.2.0` (2026-08-02),
  closing the range gate noted above.
- Added `@types/node` so `scripts/check-readme-version.ts` typechecks under
  `astro check`.
- Added GitHub support templates for pull requests and issue intake (bug
  reports, docs updates, release-readiness checks, and configuration/CI drift).
- Added `npm run check` as the repository validation gate.
- Expanded Codex operating guidance for release checks, documentation standards,
  config cleanup, metadata review, and handoff reporting.
- Standardized AI-agent coordination rules and Codex release-agent procedures.
- Documented `npm run typecheck` across contributor and agent validation
  guidance.
- Added Claude Code and Google Jules agent configuration for the workspace.
- Updated Codex guidance to coordinate with Claude Code and Jules.
- Added Codex release-agent guidance and release checklists for production
  handoff.
- Clarified AI operating roles for Claude Code and Codex.
- Added dedicated GitHub Copilot guidance in `COPILOT.md` and
  `.github/copilot-instructions.md`.
- Standardized agent boundary documentation to include Copilot support scope and
  Jules automated maintenance scope.
- Updated contributor documentation to preserve PHCDevworks company-first
  positioning.
- Pinned the direct Vite dev dependency to the Astro-compatible Vite 7 line.
- Standardized repository documentation and project-level workspace settings for
  Spectre.
