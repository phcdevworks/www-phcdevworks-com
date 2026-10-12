# PHCDevworks Website Roadmap

`www-phcdevworks-com` is the flagship public website for PHCDevworks. It
presents the company, its ecosystem, and its technical initiatives. Spectre is
the primary platform under that umbrella, not the whole identity of the site.

This document tracks what is next. For release-relevant delivery detail, see
[CHANGELOG.md](CHANGELOG.md) and git history.

---

## Foundation Status — In Progress

**Starter rebuild (2026-10-12):** the previous implementation was removed and
the site was re-scaffolded from the `@phcdevworks/spectre-init` 1.5.0 `astro`
template, with an app-level `spectre.manifest.json` validated by
`@phcdevworks/spectre-manifest` 2.0.0. The rebuilt site is a single starter
page; site content, deployment, and the typecheck step must be restored on
the new base (see "Starter Rebuild Follow-Ups" in [TODO.md](TODO.md)).

Current Spectre dependency versions: `@phcdevworks/spectre-tokens ^4.13.0`,
`@phcdevworks/spectre-ui ^5.5.0`, `@phcdevworks/spectre-ui-astro ^4.12.0` —
matching `project-design`'s latest published releases.

### What is in place

- Astro 7 starter from `@phcdevworks/spectre-init` with a working local dev
  and production build path (static output, no hosting adapter yet).
- Full validation gate: `npm run check` runs the production build and
  `spectre.manifest.json` validation before any handoff.
- Spectre-first agent guidance (Core Rules, Spectre Packages, Spectre-First
  Building, Source of Truth, Human Approval Boundaries, Standard Handoff) and
  the installed Spectre manifest as the package reference for AI agents.
- Multi-agent team (Claude Code, Codex, Copilot, Jules, Grok) with documented
  authority boundaries.

---

## Delivered Phases (previous implementation)

| Phase | Summary |
| --- | --- |
| 1 | Site foundation — SSR hosting, shared layout, navigation, footer, homepage, initial product routes, Spectre-based styling, validation gate, and repository guidance |
| 2 P0 | Content depth — Spectre Shell and Spectre WordPress expanded to structural parity with Spectre Design; homepage and route copy reframed company-first |

The page content from these phases was removed with the previous
implementation and is rebuilt on the starter as part of the follow-ups above.

---

## What's Next

1. **Content rebuild** — homepage, product routes, header, footer, and
   metadata rebuilt from `spectre-ui-astro` components, company-first.
2. **Brand expression decision** — stock Spectre theming or an approved site
   brand layer for `BRAND.md` identity.
3. **Deployment and gate restoration** — hosting adapter, deploy script, and
   a typecheck step once the toolchain supports TypeScript 7.

Any new phase must preserve the company-first positioning, use Spectre packages
and patterns before custom alternatives, remain Astro-first, and define a
focused validation path before implementation begins.

---

## Explicitly Out of Scope

- Upstream token definitions — owned by `@phcdevworks/spectre-tokens`.
- A parallel design system disconnected from Spectre.
- Generic marketing filler, decorative stock imagery, or SaaS-template layouts.
- Blog, CMS integration, or content management unless explicitly requested.
- Moving this repository toward a single-product Spectre identity.
