# PHCDevworks Website

`www-phcdevworks-com` is the public company website for PHCDevworks. It
serves as the web presence for the company, its products, its technical
ecosystem, and its broader brand — showcasing Spectre prominently without
being framed as a single-product website.

Maintained by [PHCDevworks](https://go.phcdev.co). It represents PHCDevworks
as a company first, with Spectre as one platform within that story rather
than the whole story.

## Repository Snapshot

| Field | Value |
| --- | --- |
| Project team | `project-web` |
| Repository role | PHCDevworks public company website |
| Package/artifact | `www-phcdevworks-com` |
| Current version/status | 0.0.1 |

## Standard Workflow

1. Read [AGENTS.md](AGENTS.md), then the agent-specific guide for the task.
2. Check [TODO.md](TODO.md) and [ROADMAP.md](ROADMAP.md) for current scope.
3. Make the smallest repo-local change that satisfies the task.
4. Run `npm run check` when validation is required or practical.
5. Update docs and [CHANGELOG.md](CHANGELOG.md) only when behavior, public
   contracts, or release-relevant metadata changed.

## Documentation Map

| Guide | Path |
| --- | --- |
| Agent rules | [AGENTS.md](AGENTS.md) |
| Claude Code | [CLAUDE.md](CLAUDE.md) |
| Codex | [CODEX.md](CODEX.md) |
| Copilot | [COPILOT.md](COPILOT.md) |
| Jules | [JULES.md](JULES.md) |
| Roadmap | [ROADMAP.md](ROADMAP.md) |
| Todo | [TODO.md](TODO.md) |
| Changelog | [CHANGELOG.md](CHANGELOG.md) |
| Security | [SECURITY.md](SECURITY.md) |

[![GitHub issues](https://img.shields.io/github/issues/phcdevworks/www-phcdevworks-com)](https://github.com/phcdevworks/www-phcdevworks-com/issues)
[![GitHub pulls](https://img.shields.io/github/issues-pr/phcdevworks/www-phcdevworks-com)](https://github.com/phcdevworks/www-phcdevworks-com/pulls)
[![License](https://img.shields.io/github/license/phcdevworks/www-phcdevworks-com)](LICENSE)

`www-phcdevworks-com` is the public company website for PHCDevworks.

It serves as the web presence for the company, its products, its technical
ecosystem, and its broader brand. The site may showcase Spectre prominently, but
it is not limited to Spectre and should not be framed as a single-product
website.

**Repository docs:** [CONTRIBUTING.md](CONTRIBUTING.md) |
[CHANGELOG.md](CHANGELOG.md) | [ROADMAP.md](ROADMAP.md) |
[SECURITY.md](SECURITY.md) | [BRAND.md](BRAND.md) | [AGENTS.md](AGENTS.md) |
[CLAUDE.md](CLAUDE.md) | [CODEX.md](CODEX.md) | [JULES.md](JULES.md) |
[COPILOT.md](COPILOT.md) | [LICENSE](LICENSE)

## Overview

This repository contains the Astro-based marketing and company website for
PHCDevworks.

It is responsible for presenting the company clearly and credibly across areas
such as:

- company positioning
- product and ecosystem visibility
- technical capabilities
- brand communication
- public-facing pages, calls to action, and supporting content

Spectre is part of that story, but this repository represents the broader
PHCDevworks identity and should be maintained with that scope in mind.

## Where It Fits

This site is the flagship public website for PHCDevworks. It depends on
`@phcdevworks/spectre-ui` and `@phcdevworks/spectre-ui-astro` for
Spectre-aligned presentation, but it does not define upstream design tokens or
UI package internals.

## When To Use This Repository

- Maintain the PHCDevworks public company website.
- Update contributor-facing repository docs.
- Adjust site build, preview, deployment, or workspace configuration.
- Keep automation guidance aligned across Claude Code, Codex, Copilot, and
  Jules.

## When Not To Use This Repository

- Do not define Spectre token contracts here.
- Do not implement source components for `@phcdevworks/spectre-ui`.
- Do not narrow company-wide positioning to a single-product Spectre framing —
  see `AGENTS.md` and `BRAND.md`.

## Stack

- Astro
- TypeScript
- Tailwind CSS
- Cloudflare adapter
- `@phcdevworks/spectre-ui`
- `@phcdevworks/spectre-ui-astro`

## Getting Started

### Prerequisites

- Node.js 22.12 or newer
- npm

### Install

```bash
npm install
```

### Run

```bash
npm run dev
```

## Available Scripts

| Script | What it does |
| --- | --- |
| `npm run dev` | Start the local Astro development server |
| `npm run build` | Create the production build |
| `npm run typecheck` | Run the Astro TypeScript checker (`astro check`) |
| `npm run check` | Full validation gate — runs `npm run build` then `npm run typecheck` |
| `npm run preview` | Build and start a local Cloudflare Workers preview |
| `npm run generate-types` | Refresh Wrangler type output |
| `npm run deploy` | Build and deploy to Cloudflare |

## Validation

```bash
npm run check
```

`npm run check` runs the production build then the Astro typecheck. Use it
before any handoff. `npm run preview` builds and starts a local Cloudflare
Workers preview — use this only when you need to verify Cloudflare runtime
behavior specifically.

## Troubleshooting

**Build fails with missing module errors** — run `npm install` first; `dist/`
is not committed and must be rebuilt locally.

**`npm run preview` or `npm run deploy` fails** — these require Wrangler
authentication. Run `wrangler login` and confirm you have Cloudflare access for
this project before using them.

**`npm run generate-types` produces nothing** — run `npm run build` first;
Wrangler type generation requires a compiled output to inspect.

## Project Structure

| Path | Responsibility |
| --- | --- |
| `src/pages/` | Routes (index, spectre-design, spectre-shell, spectre-wordpress) |
| `src/layouts/` | Shared Astro layout (`Layout.astro`) |
| `src/styles/` | Global CSS layered on top of Spectre |
| `src/assets/` | Site-owned static assets bundled by Astro |
| `public/` | Static assets served as-is |

## AI And Automation Boundaries

- Claude Code leads primary implementation. See [CLAUDE.md](CLAUDE.md).
- Codex handles documentation, releases, production stabilization, repo hygiene,
  and config standardization. See [CODEX.md](CODEX.md).
- GitHub Copilot provides general development assistance. See
  [COPILOT.md](COPILOT.md) and
  [.github/copilot-instructions.md](.github/copilot-instructions.md).
- Google Jules handles small automated maintenance. See [JULES.md](JULES.md).
- Follow `BRAND.md` before changing public site structure, copy, or visual
  direction.

All AI agents with repository access (Claude Code, Codex, Copilot, Jules)
have commit, push, and tag authority in this repository. Site deployment
(`npm run deploy`) remains Bradley Potts's sole authority. See
[AGENTS.md](AGENTS.md) for the full commit-policy and release-authority
grant.

Shared coordination rules live in [AGENTS.md](AGENTS.md).

## Versioning And Release Notes

Track release-relevant documentation, workflow, and configuration changes in
[CHANGELOG.md](CHANGELOG.md).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

See [LICENSE](LICENSE).

## Ownership

PHCDevworks owns and maintains this repository. This repository should use
PHCDevworks company-first naming and positioning consistently across docs,
settings, and project configuration. Spectre is part of the PHCDevworks
ecosystem, not the sole identity of this site.
