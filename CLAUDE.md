# CLAUDE.md - PHCDevworks Website

## Project Identity

**Repository:** `www-phcdevworks-com`  
**Brand:** PHCDevworks  
**Human owner:** Bradley Potts — final authority for commits, merges, tags, and releases  
**Primary AI developer:** Claude Code  
**Release and production safety:** OpenAI Codex  
**Automated maintenance:** Google Jules

`www-phcdevworks-com` is the public company website for PHCDevworks. It may
showcase Spectre prominently, but this repository represents the broader
PHCDevworks company, ecosystem, and public web presence.

This file is the authoritative guide for Claude Code operating in this
repository. Read it with `AGENTS.md`, `BRAND.md`, and `CODEX.md` before changing
public pages, project workflow, or release-sensitive configuration.

## Multi-Agent Team

`AGENTS.md` is the shared guide for agent roles, edit boundaries, and coordination rules. Claude Code leads implementation; resolve role conflicts by referencing `AGENTS.md`.

## Core Rule

Keep this site company-first.

Spectre is part of the PHCDevworks ecosystem, not the full identity of the site.
Do not frame this repository as the Spectre website alone.

## Development Workflow

```bash
npm install
npm run dev
npm run build
```

Use `npm run preview` when a page or routing change needs a Cloudflare runtime
check — this builds first and serves via `wrangler dev`, reflecting the actual
Cloudflare Workers SSR runtime. Use `npm run deploy` only when the human
explicitly requests deployment.

**Runtime context:** This site runs as an SSR application on Cloudflare Workers
via `@astrojs/cloudflare`. Node.js APIs are not available at runtime unless
explicitly enabled via Cloudflare Workers compatibility flags. Prefer
platform-agnostic or Web API patterns in server-side code.

## Validation

Run before handoff:

```bash
npm run check
```

`npm run check` is the full validation gate and currently runs `npm run build`
then `npm run typecheck`.

`npm run build` — catches Astro compilation errors, import resolution failures,
and type errors surfaced during the build.\
`npm run typecheck` (`astro check`) — runs the Astro TypeScript checker
independently of the build; catches component prop mismatches, type errors, and
TS configuration issues without producing a build artifact.

`eslint.config.ts` is present with TypeScript ESLint rules and `typescript-eslint`
is installed. Linting `.astro` files requires `eslint-plugin-astro` and
`astro-eslint-parser` — these are not yet installed. There is no `npm run lint`
script. Do not run ESLint on `.astro` files until those plugins are added. Flag
this in the handoff if linting is needed for a task.

## Implementation Priorities

1. Respect PHCDevworks positioning and `BRAND.md`.
2. Use Spectre Tokens, Spectre UI, and Spectre UI Astro before custom patterns.
3. Keep Astro-first, SSR-friendly, and maintainable.
4. Favor focused changes over broad redesigns.
5. Keep public copy concise, technical, and specific.
6. Keep documentation synchronized with actual scripts and workflow.

## Source Layout

```text
src/
  pages/          — routes (index, spectre-design, spectre-shell, spectre-wordpress)
  layouts/        — shared Astro layout (Layout.astro)
  styles/         — global CSS layered on top of Spectre
  assets/         — site-owned static assets bundled by Astro
public/           — static assets served as-is (no processing)
```

Add `src/components/` when reusable components are introduced.

## Edit Boundaries

| Path                                                       | Status                                                     |
| ---------------------------------------------------------- | ---------------------------------------------------------- |
| `src/pages/`                                               | May edit for route and page work                           |
| `src/layouts/`                                             | May edit for shared layout structure                       |
| `src/styles/`                                              | May edit for site-level styling layered on Spectre         |
| `public/`                                                  | May edit for site-owned static assets                      |
| `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, agent docs | May edit when workflow, scope, or release guidance changes |
| `package.json`, `package-lock.json`                        | Edit only for intentional script or dependency changes     |
| `dist/`, `.astro/`, `node_modules/`, `.wrangler/`          | Do not hand-edit                                           |

Do not add dependencies unless the task truly requires them and the reason is
clear in the handoff.

## Brand And Content Rules

- Follow `BRAND.md` for visual identity decisions.
- Use dark, technical, high-contrast, typography-first layouts.
- Keep `#EE005A` as the primary accent and `#012641` as the approved structural
  deep color.
- Avoid generic SaaS copy, stock-photo thinking, decorative filler, and
  over-claiming.
- Do not use button-led CTA patterns as the default for impact sections when an
  editorial route strip or text-led navigation is stronger.

## Git Access — Denied

**Claude Code has zero git access in this repo, as part of a companywide
policy.** Claude Code must not run `git commit`, `git push`, `git tag`, or
any other git command — read-only or mutating — here. This supersedes any
prior commit/push/tag grant described in this repo's `AGENTS.md`. OpenAI
Codex now executes all git operations for this repo; see `AGENTS.md` and
`CODEX.md`.

When work is ready, Claude Code stops short of any git command and hands off
to Codex (or Bradley Potts) with a summary of files changed and validation
performed (`npm run check`).

## Handoff Expectations

Every handoff should include:

- what changed
- why it matters
- files touched
- validation performed
- known risks or follow-up

Keep handoffs short and release-oriented.
