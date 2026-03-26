# Spectre Website

[![GitHub issues](https://img.shields.io/github/issues/phcdevworks/www-phcdevworks-com)](https://github.com/phcdevworks/www-phcdevworks-com/issues)
[![GitHub pulls](https://img.shields.io/github/issues-pr/phcdevworks/www-phcdevworks-com)](https://github.com/phcdevworks/www-phcdevworks-com/pulls)
[![License](https://img.shields.io/github/license/phcdevworks/www-phcdevworks-com)](LICENSE)

`www-phcdevworks-com` is the public website for Spectre, run by PHCDevworks. It
represents the product, brand, and ecosystem at the project level.

**Repository docs:** [CONTRIBUTING.md](CONTRIBUTING.md) |
[CHANGELOG.md](CHANGELOG.md) | [SECURITY.md](SECURITY.md) |
[LICENSE](LICENSE)

## Overview

This repository contains the Astro-based flagship web presence for Spectre. It
should stay aligned with the documentation repository in naming, contributor
guidance, and project-level settings.

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

- `npm run dev` starts the local Astro development server.
- `npm run build` creates the production build.
- `npm run preview` builds the project and starts the Cloudflare preview.
- `npm run generate-types` refreshes Wrangler type output.
- `npm run deploy` builds and deploys the site.

## Project Structure

| Path | Responsibility |
| --- | --- |
| `src/pages/` | Route-level pages for the public website |
| `src/components/` | Shared presentation components |
| `public/` | Static assets served as-is |

## Spectre Repositories

- [spectre-tokens](https://github.com/phcdevworks/spectre-tokens)
- [spectre-ui](https://github.com/phcdevworks/spectre-ui)
- [spectre-ui-astro](https://github.com/phcdevworks/spectre-ui-astro)
- [docs-phcdevworks-com](https://github.com/phcdevworks/docs-phcdevworks-com)
- [www-phcdevworks-com](https://github.com/phcdevworks/www-phcdevworks-com)

## Ownership

Spectre is run by PHCDevworks. This repository should use Spectre naming and
PHCDevworks ownership language consistently across docs, settings, and project
configuration.
