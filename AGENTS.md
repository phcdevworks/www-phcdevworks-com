# www-phcdevworks-com Agent Guide

## Project Identity

- Repository: `www-phcdevworks-com`
- Brand: PHCDevworks
- Maintainer: PHCDevworks
- Scope: public company website, supporting content, and project-level website
  configuration

## Mission

Build and maintain the flagship public website for PHCDevworks.

This repository represents the company first. It may showcase Spectre and other
PHCDevworks initiatives prominently, but it must not be framed as a
single-product website.

## AI Operating Model

This repository follows a lead-and-check model for AI-assisted work:

| Agent          | Role                                                                                                        | Authority                                          |
| -------------- | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| Claude Code    | Lead implementation agent for primary development work                                                      | `CLAUDE.md` when present, then `AGENTS.md`         |
| OpenAI Codex   | Release agent for production readiness, documentation, repo hygiene, focused refactors, and standardization | `CODEX.md`, then `AGENTS.md`                       |
| GitHub Copilot | General development support assistant                                                                       | `COPILOT.md` and `.github/copilot-instructions.md` |
| Google Jules   | Automated maintenance for small fixes, dependency micro-updates, and bounded documentation sync             | `JULES.md`, then `AGENTS.md`                       |

Claude Code leads implementation. Codex keeps work aligned, checks production
readiness, updates documentation when workflows drift, and refactors only when
required for maintainability or release safety. Copilot supports in-editor
development tasks without ownership authority. Jules handles bounded automated
maintenance only and must not take over primary development, brand direction,
release ownership, or broad refactors.

Human final review and commit authority stays with PHCDevworks maintainers.

## Positioning

This repository represents:

- PHCDevworks as the parent company and operating brand
- the broader PHCDevworks ecosystem
- products, systems, and technical initiatives under that umbrella
- Spectre as a major platform within that story, not the entire story

## Working Rules

- Keep naming consistent with PHCDevworks and current company positioning.
- Treat this site as a downstream Spectre application where appropriate.
- Reuse Spectre packages and patterns where appropriate instead of inventing a
  parallel design system.
- Prefer building with Spectre Tokens, Spectre UI, and Spectre UI Astro first,
  then layer custom site styling after the system structure is in place.
- Keep Astro-first, SSR-friendly, and maintainable.
- Prefer clarity, maintainability, and strong structure over novelty.
- Favor small, reviewable changes over broad rewrites.
- Do not add unnecessary dependencies.
- Do not rewrite unrelated files.
- Do not carry forward retired branding, old organization names, or narrow
  single-product framing.
- Follow `BRAND.md` for visual identity decisions.
- Follow `CLAUDE.md` for Claude Code implementation leadership.
- Follow `CODEX.md` for Codex release-agent responsibilities.
- Follow `JULES.md` for bounded automated maintenance tasks.

## Content Rules

- Keep contributor-facing Markdown concise and accurate.
- Make repository docs match the actual scripts and workflow.
- Keep public-facing messaging company-first, technically credible, and concise.
- Do not describe this repository as the Spectre website alone.
- Present Spectre as part of the PHCDevworks ecosystem, not the sole identity of
  the site.
- Avoid vague marketing filler, bloated copy, startup clichés, and
  over-claiming.
- When the page voice goes raw, rebellious, or anti-corporate, keep it sharp and
  intentional instead of sliding back into polite SaaS copy.
- Do not default to button-led CTA patterns on impact sections or the homepage.
  Prefer route strips, editorial links, or other non-corporate navigation
  treatments when that direction is active.
- Do not use weak anti-corporate slogans as filler taglines. If the copy is
  blunt, it still needs to be legible, specific, and supported by clean page
  structure.

## Codex Release Agent

Codex is looped in to keep changes production-ready. In this repository, Codex
should:

- keep tabs on local changes and release impact
- review Claude Code work for brand, docs, accessibility, and build readiness
- update documentation for standardization when scripts or workflow change
- perform focused refactors when they reduce drift or release risk
- check Markdown-heavy changes with the same care as code changes
- keep `CHANGELOG.md` useful for release review when changes are
  release-relevant

Codex should not replace Claude Code as implementation lead unless the human
explicitly asks Codex to take over a task.

## Google Jules Maintenance Agent

Jules is the automated maintenance agent for this repository. Jules should:

- fix small documentation drift, typos, and broken internal links
- perform dependency micro-updates only within compatible major lines
- keep maintenance tasks atomic and easy to review
- run `npm run build` when practical before reporting completion
- stop and report blockers when validation fails outside Jules scope

Jules must not own broad redesigns, architecture decisions, release cuts,
deployment, or changes that alter PHCDevworks brand direction.

## Configuration Rules

- Preserve project-level settings only.
- Favor shared editor behavior over personal theme, font, or UI preferences.
- Keep line endings, indentation, and save behavior aligned with
  `.editorconfig`, `.gitattributes`, and local workspace settings.
- Do not introduce unnecessary dependencies or unrelated configuration churn.

## Repo Ownership

This repository owns:

- company website information architecture
- page composition and route structure
- homepage and public-facing marketing pages
- site-specific content sections and messaging
- navigation, footer, calls to action, and supporting pages
- company-level presentation of products, platforms, and ecosystem initiatives

This repository does not own:

- upstream token definitions
- a separate visual language disconnected from Spectre
- generic marketing fluff
- decorative imagery used to compensate for weak layout or copy

## Working Priorities

1. homepage structure and messaging
2. reusable layout foundation
3. header and footer
4. ecosystem and product visibility
5. clear calls to action
6. responsive polish
7. accessibility
8. metadata and SEO
9. performance and maintainability

## Verification

- Run `npm run build` after documentation or config changes when practical.
- Check for broken internal links in repository Markdown before finishing.
- Keep changes easy to review and grounded in the current repo structure.
- Use `.codex/release-checklist.md` before production release or final release
  handoff.

## Execution Style

Prefer one meaningful improvement at a time.

Examples of good pull requests:

- add base layout
- add site header and footer
- create homepage hero and section structure
- improve CTA clarity
- add metadata
- tighten copy on a single page
- improve accessibility in one focused area

Examples of bad pull requests:

- redesign everything at once
- add random dependencies
- mix unrelated cleanup into one diff
- introduce off-brand visual experiments
- add imagery that breaks the typography-first direction
- replace the dark technical visual language with generic SaaS styling

## Pull Request Expectations

Each pull request should:

- stay narrowly scoped
- explain what changed
- explain why it matters
- list files changed
- note assumptions if any
- recommend the next logical follow-up

## Definition of Done

A change is done when:

- it keeps the site aligned with PHCDevworks company positioning
- it respects the visual rules in `BRAND.md`
- it avoids unnecessary drift from Spectre
- it improves clarity, structure, accessibility, performance, or maintainability
- the diff is easy to review

## Default Decision Rule

When in doubt:

- choose clarity over cleverness
- choose hierarchy over decoration
- choose restraint over noise
- choose maintainability over novelty
- choose company-level framing over single-product framing
