# CLAUDE.md - PHCDevworks Website

## Project Identity

**Repository:** `www-phcdevworks-com`  
**Brand:** PHCDevworks  
**Primary AI developer:** Claude Code  
**Release support:** OpenAI Codex  
**Automated maintenance:** Google Jules

`www-phcdevworks-com` is the public company website for PHCDevworks. It may
showcase Spectre prominently, but this repository represents the broader
PHCDevworks company, ecosystem, and public web presence.

This file is the authoritative guide for Claude Code operating in this
repository. Read it with `AGENTS.md`, `BRAND.md`, and `CODEX.md` before changing
public pages, project workflow, or release-sensitive configuration.

## Multi-Agent Team

| Agent          | Role                                                                                                          | Guide                                              |
| -------------- | ------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| Claude Code    | Lead implementation agent for primary development, page structure, site composition, and integration work     | `CLAUDE.md`                                        |
| OpenAI Codex   | Release readiness, production stabilization, documentation hygiene, repo hygiene, and focused refactor review | `CODEX.md`                                         |
| Google Jules   | Bounded automated maintenance, dependency micro-updates, typo fixes, and small documentation sync tasks       | `JULES.md`                                         |
| GitHub Copilot | General development support assistant for in-editor productivity and targeted implementation help             | `COPILOT.md` and `.github/copilot-instructions.md` |

`AGENTS.md` is the shared repository guide. Treat Codex reviews and Jules
maintenance changes as peer input. Claude Code keeps implementation leadership
unless the human explicitly assigns a task to another agent.

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
check. Use `npm run deploy` only when the human explicitly requests deployment.

## Implementation Priorities

1. Respect PHCDevworks positioning and `BRAND.md`.
2. Use Spectre Tokens, Spectre UI, and Spectre UI Astro before custom patterns.
3. Keep Astro-first, SSR-friendly, and maintainable.
4. Favor focused changes over broad redesigns.
5. Keep public copy concise, technical, and specific.
6. Keep documentation synchronized with actual scripts and workflow.

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

## Working With Codex

Codex acts as release agent and backup reviewer. Before handoff, invite Codex to
check:

- build readiness
- documentation drift
- brand and company-first framing
- accessibility risks
- dependency or configuration churn
- release notes and changelog accuracy

If Codex flags a production issue, resolve it or document why it is
intentionally deferred.

## Working With Jules

Jules may handle small maintenance tasks when the scope is bounded and
validation is clean. Jules must not own broad redesigns, architecture decisions,
release decisions, or major dependency migrations.

Claude Code should review Jules changes for scope, brand alignment, and build
readiness before they are treated as production-ready.

## Handoff Expectations

Every handoff should include:

- what changed
- why it matters
- files touched
- validation performed
- known risks or follow-up

Keep handoffs short and release-oriented.
