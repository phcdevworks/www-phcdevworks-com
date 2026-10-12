# CLAUDE.md - PHCDevworks Website

## Verified TODO Completion Workflow

For every TODO item Claude Code completes, use this sequence in the same change:

1. Keep the item in `TODO.md` while implementation or verification is in progress.
2. Confirm every acceptance criterion is met and the repository's required tests and validation gate pass.
3. Only after verification passes, remove the completed item from `TODO.md` immediately; do not leave it active or checked off.
4. Update `CHANGELOG.md` under `[Unreleased]` as usual, update the applicable `ROADMAP.md` shipped/status table and phase text, and update every other affected status or dependency reference.

If implementation is incomplete or any required check fails, keep the TODO item open and do not describe the work as shipped.

## Project Identity

**Repository:** `www-phcdevworks-com`\
**Brand:** PHCDevworks\
**Human owner:** Bradley Potts — final authority for commits, merges, tags, and releases\
**Primary AI developer:** Claude Code\
**Release and production safety:** OpenAI Codex\
**Automated maintenance:** Google Jules\
**Development assistance:** GitHub Copilot, xAI Grok (incl. Grok Bot)

`www-phcdevworks-com` is the public company website for PHCDevworks. It may
showcase Spectre prominently, but this repository represents the broader
PHCDevworks company, ecosystem, and public web presence.

This file is the authoritative guide for Claude Code operating in this
repository. Read it with `AGENTS.md`, `BRAND.md`, and `CODEX.md` before changing
public pages, project workflow, or release-sensitive configuration.

## Multi-Agent Team

`AGENTS.md` is the shared guide for agent roles, edit boundaries, and coordination rules. Claude Code leads implementation; resolve role conflicts by referencing `AGENTS.md`.

## The One Rule That Overrides Everything

The site owns the company story; Spectre owns the system. If a change needs a
token, recipe, or component that the published packages do not provide, stop
and request it upstream instead of solving it here.

Keep this site company-first. Spectre is part of the PHCDevworks ecosystem,
not the full identity of the site. Do not frame this repository as the
Spectre website alone.

The site was scaffolded from the `@phcdevworks/spectre-init` `astro` template
and carries an app-level [spectre.manifest.json](spectre.manifest.json)
validated by `@phcdevworks/spectre-manifest`.

## Standard Procedure

1. Confirm the task does not cross a human approval boundary in
   [AGENTS.md](AGENTS.md).
2. Read the installed Spectre manifest
   (`node_modules/@phcdevworks/spectre-manifest/spectre.manifest.json`) and the
   relevant `spectre-ui-astro` component contract before writing markup.
3. Inspect the relevant page or layout fully before editing.
4. Follow the Spectre-First Building order in [AGENTS.md](AGENTS.md); prefer
   component APIs and shipped classes, and remove any local code they
   supersede.
5. Implement the smallest correct change.
6. Run `npm run check`.
7. State whether a rendered-page review is still needed for the touched pages.
8. Hand off files changed, validation results, and remaining risk.

## Development Workflow

```bash
npm install
npm run dev
npm run build
```

`npm run preview` serves the production build locally. The starter builds
static output and has no hosting adapter or deploy script yet; restoring
deployment is tracked in [TODO.md](TODO.md) and stays Bradley Potts's call.

## Validation

Run before handoff:

```bash
npm run check
```

`npm run check` is the full validation gate. It runs `npm run build` then
`npm run manifest:validate`.

`npm run build` — catches Astro compilation errors and import resolution
failures.\
`npm run manifest:validate` (`spectre-manifest-validate
spectre.manifest.json`) — confirms the app manifest is valid against the
published schema.

`astro check` is not in the gate: `@astrojs/check` does not yet support the
starter's TypeScript 7. `eslint.config.ts` is present, but ESLint and
`typescript-eslint` are not installed and there is no `npm run lint` script,
so the config is not enforced. Both are tracked in [TODO.md](TODO.md).

## Implementation Priorities

1. Respect PHCDevworks positioning and `BRAND.md`.
2. Use Spectre Tokens, Spectre UI, and Spectre UI Astro before custom patterns.
3. Keep Astro-first and maintainable.
4. Favor focused changes over broad redesigns.
5. Keep public copy concise, technical, and specific.
6. Keep documentation synchronized with actual scripts and workflow.

## Implementation Rules

- Spectre components, variants, and shipped classes own visual consistency.
  Default to zero site-authored CSS; any exception needs Bradley Potts's
  approval.
- Never declare or shadow a `--sp-*` token.
- Do not reproduce Spectre typography, spacing, layout, surface, radius,
  shadow, state, or responsive recipes under local classes.
- Do not style rendered component internals. Use the component's public API;
  if it is insufficient, route the reusable need upstream.
- Delete obsolete markup, classes, and styles when a component or utility
  takes over their job.
- Keep `spectre.manifest.json` in sync with `package.json` whenever an
  `@phcdevworks/*` dependency is added, removed, or bumped.

## Escalate Instead of Deciding

Stop and ask Bradley Potts before:

- adding site-authored CSS or a site-level brand layer
- changing brand colors or the primary typeface
- adding a hosting adapter, deploy script, or dependency outside the starter
  and published Spectre packages
- taking release or deploy actions

## Source Layout

| Path                    | Responsibility                                            |
| ----------------------- | --------------------------------------------------------- |
| `src/pages/`            | Route-level Astro pages                                   |
| `src/layouts/`          | Page layouts; `BaseLayout.astro` imports `spectre-ui` CSS |
| `astro.config.ts`       | Astro configuration (starter default, no adapter yet)     |
| `spectre.manifest.json` | App manifest describing this site's Spectre dependencies  |
| `eslint.config.ts`      | TypeScript-ESLint rules — ESLint is not installed yet     |
| `tsconfig.json`         | Extends `astro/tsconfigs/strict`                          |
| `.codex/`               | Codex release-checklist and Markdown standards            |

Add `src/components/` only when a site-level composition repeats across pages
and no `spectre-ui-astro` component expresses it.

## Edit Boundaries

| Path                                                       | Status                                                     |
| ---------------------------------------------------------- | ---------------------------------------------------------- |
| `src/pages/`                                               | May edit for route and page work                           |
| `src/layouts/`                                             | May edit for shared layout structure                       |
| `spectre.manifest.json`                                    | Edit with care; keep in sync with `package.json`           |
| `astro.config.ts`, `tsconfig.json`                         | Starter-owned; change only with an explicit reason         |
| `README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, agent docs | May edit when workflow, scope, or release guidance changes |
| `package.json`, `package-lock.json`                        | Edit only for intentional script or dependency changes     |
| `dist/`, `.astro/`, `node_modules/`                        | Do not hand-edit                                           |

Do not add dependencies unless the task truly requires them and the reason is
clear in the handoff.

## Brand And Content Rules

- Follow `BRAND.md` for visual identity decisions.
- Use dark, technical, high-contrast, typography-first layouts.
- Keep `#EE005A` as the primary accent and `#012641` as the approved structural
  deep color. Express them through Spectre's published themes and APIs — not
  through site-authored CSS — until Bradley Potts approves a site brand layer.
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
- Spectre fidelity impact (components used, any local markup or CSS added or
  removed)
- whether a rendered-page review is still needed
- known risks or follow-up

Keep handoffs short and release-oriented.
