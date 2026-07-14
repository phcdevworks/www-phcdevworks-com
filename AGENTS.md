# www-phcdevworks-com Agent Guide

## Repository Snapshot

| Field | Value |
| --- | --- |
| Project team | `project-web` |
| Repository role | PHCDevworks public company website |
| Package/artifact | `www-phcdevworks-com` |
| Validation gate | `npm run check` |

## Standard Authority Model and Handoff

See the project-team [AGENTS.md](../AGENTS.md) "AI Operating Model" and
"Handoff Requirements" sections for the full agent roster, authority table,
and standard handoff format. Bradley Potts holds final authority for commits,
merges, tags, publishing, and releases. Do not edit generated outputs
directly. Do not update [CHANGELOG.md](CHANGELOG.md) unless the change is
release-relevant.

## Project Identity

- Repository: `www-phcdevworks-com`
- Brand: PHCDevworks
- Maintainer: PHCDevworks
- Scope: public company website, supporting content, and project-level website
  configuration

## Cross-Repo Access

This repo may be worked on standalone or alongside any combination of other
PHCDevworks repos — do not assume the company root or sibling project areas
are present. The following rules are self-contained and apply whether or not
that broader context is available.

**File access.** An agent working in this repo has full read/write access to
every file in this repo. When this repo is present alongside other
PHCDevworks repos (company root or sibling `project-*` areas), the same full
read/write access extends to those repos too — there is no per-repo access
restriction anywhere in this workspace. What differs repo-to-repo is not
*access*, it's *editorial ownership*: each repo's own `CLAUDE.md`/`AGENTS.md`
still governs what changes make sense there (design-token authority, layer
boundaries, etc.) — being able to open and edit a file is not the same as it
being this repo's job to change it.

**Cross-repo changelog sync.** When a change in this repo has direct
downstream or upstream impact on another present repo (e.g. a breaking token
rename, an API contract change), an agent may append a `CHANGELOG.md
[Unreleased]` entry directly into that other repo's own changelog — not just
leave a note asking its owner to add it. Rules:

1. Only append new `[Unreleased]` entries — never edit, reorder, or remove
   another repo's existing changelog entries, version headers, or release
   history.
2. Every cross-repo entry must be self-contained and attributed: which repo
   caused it and why, what changed from the affected repo's perspective, and
   the date added.
3. Add it in the same change that produced the impact, not a later session.
4. This never grants release authority — cutting a release, bumping a version
   header, or publishing a package stays gated by that repo's own release
   process and the human owner's final sign-off.

**TODO/roadmap requests.** When work here surfaces a need that belongs to
another repo, an agent may append the request directly to that repo's own
`TODO.md` under a clearly labeled "Requested by Downstream" section (create
it if absent), stating which repo is requesting it, why, the date, and a
link back if the other repo's `TODO.md`/`ROADMAP.md` is reachable.

No AI agent creates commits, tags, publishes packages, or merges changes in
this repo or any other unless that repo's own agent guide explicitly grants
that authority or the human owner has explicitly requested the action.

## Mission

Build and maintain the flagship public website for PHCDevworks.

This repository represents the company first. It may showcase Spectre and other
PHCDevworks initiatives prominently, but it must not be framed as a
single-product website.

## Agent Boundaries

- **Bradley Potts** holds final authority for all commits, merges, tags, and
  production deployments. No AI agent may commit, push, or release.
- **Claude Code** owns lead implementation and project direction.
- **OpenAI Codex** owns release readiness, production stabilization,
  documentation standardization, repo hygiene, and config standardization. Codex
  does not override Claude Code's implementation decisions.
- **ChatGPT** provides strategy guidance and external review. ChatGPT does not
  own implementation, releases, governance, or autonomous execution.
- **GitHub Copilot** is a development support assistant and does not own
  implementation direction, architecture, releases, production stabilization,
  repository governance, or automated maintenance.
- **Google Jules** owns automated micro-maintenance only. Jules does not own
  architecture decisions, brand direction, release ownership, or broad
  refactors.

When instructions appear to conflict, agent-specific guides take precedence over
this file for their own scope. Use this file for shared coordination policy.

## AI Coordination Rules

- Use `AGENTS.md` as the central coordination document for all agents.
- Use the agent-specific files for role details: `CLAUDE.md`, `CODEX.md`,
  `COPILOT.md`, and `JULES.md`.
- Resolve role conflicts by preserving the operating model above: Claude Code
  leads implementation, Codex owns release/documentation/stabilization support,
  Copilot assists, and Jules handles bounded automated maintenance.
- Keep shared project rules in `AGENTS.md`; keep agent-specific workflow details
  in the matching agent file.
- Update related agent docs together when scripts, validation gates, or
  ownership boundaries change.

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
- All `scripts/` tooling is TypeScript (`.ts`), run via
  `node --experimental-strip-types`; never add a new `.js`/`.mjs` script.
  Convert `scripts/screenshot.js` to `.ts` if it is touched for unrelated work.

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
- Do not use weapons language.
- Do not refer to Spectre as an "8-layer" system.

## Codex Release Agent

**OpenAI Codex** owns release readiness, production stabilization,
documentation standardization, repo hygiene, and config standardization for
this repository. Codex does not replace Claude Code as implementation lead
unless the human explicitly asks Codex to take over a task. See
[CODEX.md](CODEX.md) for full responsibilities.

## Google Jules Maintenance Agent

**Google Jules** owns automated micro-maintenance only for this repository.
Jules must not own broad redesigns, architecture decisions, release cuts,
deployment, or changes that alter PHCDevworks brand direction. See
[JULES.md](JULES.md) for full task scope.

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

- Use `npm run check` as the full validation gate when practical.
- Run `npm run build` after documentation or config changes when practical.
- Run `npm run typecheck` when Astro, TypeScript, dependency, or config behavior
  changes.
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

Each pull request should:

- stay narrowly scoped
- explain what changed
- explain why it matters
- list files changed
- note assumptions if any
- recommend the next logical follow-up

## Upstream Requests and Roadmap Self-Expansion

Full directive: project-team [AGENTS.md](../AGENTS.md) "Upstream Requests and
Roadmap Self-Expansion." Applied to this repo:

- This repo's upstream is `project-design` (`spectre-tokens`, `spectre-ui`,
  `spectre-ui-astro`). If a page or section needs a token, recipe, or
  component that doesn't exist upstream, append the request to the owning
  `project-design` repo's `TODO.md` under `## Requested by Downstream`,
  dated, with the reason and a link back to this repo's own
  TODO.md/ROADMAP.md. Never hand-roll a parallel design pattern instead.
- This repo has no downstream consumer within the workspace. No `##
  Requested by Downstream` section is expected here, but keep one ready if
  that ever changes.
- This repo's own `ROADMAP.md` may be proactively expanded with new or
  reordered phases by the agent's own analysis — but never mark a phase
  delivered without `npm run check` (build + typecheck) passing, and never let
  a self-expanded phase drift the site toward single-product Spectre framing
  — this repository represents PHCDevworks company-first (see Positioning
  above).
- Surface any new TODO request or roadmap expansion in the handoff for Bradley
  Potts in the same change it was made, and reflect cross-repo-relevant
  changes in the project-team's own ROADMAP.md/TODO.md.

## Pull Request Creation

Every agent that opens a PR must populate every section of the repo's PR
template (`.github/pull_request_template.md`):

- **Summary** — describe the change and why it matters.
- **Type Of Change** — check every box that applies.
- **Package Boundary Check** — confirm the change stays within this
  repository's website scope.
- **Public API Impact** — confirm whether public behavior changed.
- **Validation** — record the command run and its result.
- **Documentation Updated** — confirm which docs were updated or note why none
  were needed.
- **Release Impact** — flag any release-relevant changes.
- **Codex Review Needed** — indicate whether Codex review is required.
- **Claude Code Implementation Notes** — add notes when relevant.

Never submit a PR with an empty body or only the template headings left
unfilled.

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

## For Full Operating Context

See the agent-specific guide for each role:

- [CLAUDE.md](CLAUDE.md) — implementation authority, project structure, content
  standards, and workflow
- [CODEX.md](CODEX.md) — release readiness checklist and documentation
  standardization
- [COPILOT.md](COPILOT.md) — Copilot support boundaries and practical guardrails
- [JULES.md](JULES.md) — maintenance task scope and commit authority
- [.github/copilot-instructions.md](.github/copilot-instructions.md) — Copilot
  IDE-facing scope and repository conventions
