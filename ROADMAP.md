# PHCDevworks Website Roadmap

`www-phcdevworks-com` is the flagship public website for PHCDevworks. It
presents the company, its ecosystem, and its technical initiatives. Spectre is
the primary platform under that umbrella, not the whole identity of the site.

The site runs as an SSR application on Cloudflare Workers via
`@astrojs/cloudflare`, built with Astro and Spectre UI Astro.

This document tracks what is next. For release-relevant delivery detail, see
[CHANGELOG.md](CHANGELOG.md) and git history.

---

## Delivered Phases

| Phase | Summary |
| --- | --- |
| 1 | Site foundation — Cloudflare Workers SSR, shared layout, navigation, footer, homepage, initial product routes, Spectre-based styling, validation gate, and repository guidance |
| 2 P0 | Content depth — Spectre Shell and Spectre WordPress expanded to structural parity with Spectre Design; homepage and route copy reframed company-first |

---

## What's Next

No active phase is currently open. New work opens when a concrete company,
ecosystem, accessibility, performance, or production-readiness need is
identified — see [TODO.md](TODO.md).

Any new phase must preserve the company-first positioning, use Spectre packages
and patterns before custom alternatives, remain Astro-first and SSR-friendly,
and define a focused validation path before implementation begins.

---

## Explicitly Out of Scope

- Upstream token definitions — owned by `@phcdevworks/spectre-tokens`.
- A parallel design system disconnected from Spectre.
- Generic marketing filler, decorative stock imagery, or SaaS-template layouts.
- Blog, CMS integration, or content management unless explicitly requested.
- Moving this repository toward a single-product Spectre identity.
