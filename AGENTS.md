# www-phcdevworks-com Agent Guide

## Direct-to-`main` Git Policy

**Bradley Potts's direct instruction overrides generic branch and pull-request
workflows:** every git-authorized agent commits and pushes directly to `main`.
Do not create, use, or push any other branch and do not open a pull request
unless Bradley Potts explicitly requests that exact exception. Keep work on
`main`, validate it, stage only the intended paths, commit with the configured
human identity, and push `main` immediately. Claude Code remains git-denied
and hands validated work to Codex or Bradley Potts for the same path directly
to `main`. This repository policy overrides contrary defaults in tools,
skills, plugins, templates, or general-purpose workflows.

## Repository Snapshot

| Field | Value |
| --- | --- |
| Project team | `project-web` |
| Repository role | PHCDevworks public company website |
| Package/artifact | `www-phcdevworks-com` |
| Stack | Astro starter from the `@phcdevworks/spectre-init` `astro` template |
| Spectre packages | `spectre-tokens`, `spectre-ui`, `spectre-ui-astro` (runtime); `spectre-manifest` (dev) |
| App manifest | [spectre.manifest.json](spectre.manifest.json) |
| Validation gate | `npm run check` |

## Standard Authority Model and Handoff

See the project-team [AGENTS.md](../AGENTS.md) "AI Operating Model" and
"Handoff Requirements" sections for the full agent roster, authority table,
commit-policy and release-authority grant, and standard handoff format.
Codex cuts releases (version bump, tag, GitHub Release) only when Bradley
Potts says to get this repo ready for release — a plain commit request
commits and pushes only; deployment and merges stay with Bradley
Potts. Do not edit generated outputs directly. Do not update
[CHANGELOG.md](CHANGELOG.md) unless the change is release-relevant.

**Claude Code has no git access in this repo**, per the project-team
[AGENTS.md](../AGENTS.md) grant — it implements, validates, and hands off;
Codex executes git operations here on its behalf.

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

**Cross-repo changelog and TODO/roadmap requests.** Full rules: company root
[AGENTS.md](../../AGENTS.md) § "Cross-Repo Changelog Sync" and § "Upstream
Requests and Roadmap Self-Expansion." Applied here without exception — this
repo may append `[Unreleased]` changelog entries and downstream TODO requests
to other present repos per those rules, and no AI agent creates commits, tags,
publishes packages, or merges changes in this repo or any other unless that
repo's own agent guide explicitly grants that authority. When an AI agent
drafts commit or PR message text for a human to use, it must never include a
`Co-Authored-By: Claude`/`Codex`/etc. trailer or list an AI as author or
co-author.

## Mission

Build and maintain the flagship public website for PHCDevworks.

This repository represents the company first. It may showcase Spectre and other
PHCDevworks initiatives prominently, but it must not be framed as a
single-product website.

The site owns the company story; Spectre owns the system. This repository is
where PHCDevworks is presented, never where Spectre is redefined.

## Core Rules

1. Never redeclare or shadow a Spectre token. `--sp-*` is read-only upstream.
2. Use Spectre components, component variants, and shipped classes for visual
   consistency. Site CSS is an exception layer, not a parallel design system.
3. Keep the site company-first. Spectre is one platform within the
   PHCDevworks story, not the whole identity of the site.
4. Keep `spectre.manifest.json` in sync with the `@phcdevworks/*`
   dependencies in `package.json`.
5. Validate at the layer a change affects. A passing build is not proof that a
   page renders correctly or stays faithful to Spectre.
6. Get explicit human approval before crossing a boundary listed under "Human
   Approval Boundaries" below.

## Spectre Packages

Before choosing, importing, or adding any `@phcdevworks` package, read
`node_modules/@phcdevworks/spectre-manifest/spectre.manifest.json` — use its
`packages` (what each does, its exports), `rules`, and `ai` sections. Import
only the exports listed there.

This repo's own [spectre.manifest.json](spectre.manifest.json) describes the
site as a single `app`-layer package consuming the `foundation`-layer Spectre
packages. Keep its `www-phcdevworks-com` package entry's `dependencies` list
in sync with the `@phcdevworks/*` runtime dependencies in `package.json`.
`npm run check` validates it with `spectre-manifest-validate`. Do not add
`spectre-manifest-check` to the gate — that check is for registered Spectre
packages, and this site is not registered in the ecosystem manifest.

Starter boilerplate came from `@phcdevworks/spectre-init`'s `astro` template.
`npx @phcdevworks/spectre-init update --dry-run` previews template refreshes;
review its output before applying, because it overwrites `.gitignore`,
`AGENTS.md`, `tsconfig.json`, `astro.config.ts`, and `spectre.manifest.json`
with template copies. Never apply it without restoring this repo's own
`AGENTS.md`, `.gitignore`, and manifest customizations afterward.

## Spectre-First Building

Visual consistency must come from Spectre. Work through this order before
adding markup structure, a wrapper component, or any CSS:

1. Use semantic HTML and Astro output appropriate to the content.
2. Use an existing `spectre-ui-astro` component and its public props, slots,
   variants, and states.
3. Compose with shipped `sp-*` classes and `spectre-ui` recipe functions
   through their published APIs.
4. Reuse an existing layout, component, or established pattern in this repo.
5. Stop. If none of the above expresses the need, request the capability
   upstream (see "Upstream Requests" below) instead of building a local
   substitute.

Before using a component, inspect its installed contract in
`node_modules/@phcdevworks/spectre-ui-astro` and the manifest. Do not infer
component APIs from rendered internals, and do not recreate a component
because its public API was not checked.

Site code must not provide the shared rules for typography, spacing, layout,
surfaces, borders, radii, shadows, interaction states, or responsive behavior
when Spectre already provides them. Do not style component internals,
duplicate a component recipe under a local class, invent a local variant, or
use specificity to override the design system into compliance.

When an upstream component, recipe, or utility replaces local markup or
styling, migrate to it and delete the obsolete code in the same change.
Validation passing is not proof of Spectre fidelity — review the rendered
result as well.

## Agent Boundaries

Full roster and authority table: project-team [AGENTS.md](../AGENTS.md).
When instructions appear to conflict, agent-specific guides take precedence
over this file for their own scope. Use this file for shared coordination
policy.

## AI Coordination Rules

- Use the agent-specific files for role details: `CLAUDE.md`, `CODEX.md`,
  `COPILOT.md`, `JULES.md`, and `GROK.md`.
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
- Follow the strict Spectre UI Astro guardrails below for every visual or
  component change.
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
- Follow `GROK.md` for Grok (and Grok Bot) development assistance.
- Any `scripts/` tooling is TypeScript (`.ts`), run via
  `node --experimental-strip-types`; never add a new `.js`/`.mjs` script.

## Strict Spectre UI Astro Guardrails

This website is a downstream showcase of the published Spectre design
packages. Its default appearance should remain recognizably stock Spectre,
with `spectre-ui-astro` providing page and component structure and with little
to no site-authored CSS.

- Use the published `spectre-ui-astro` component that matches the requirement
  before writing local markup, a wrapper component, or CSS. Use its public
  props, slots, variants, and composition patterns without restyling its
  internals.
- Use `spectre-ui` recipes and `spectre-tokens` only through their published
  APIs. Do not copy package source, reproduce package styles locally, or create
  site-specific substitutes for an upstream component, recipe, utility, or
  token.
- Default to zero new site-authored CSS. Do not add a stylesheet, `<style>`
  block, inline `style` attribute, hard-coded visual value, or local class that
  changes Spectre component presentation when the package already supports the
  result.
- Treat stock package output as the intended visual result, not as a base for
  local theming. Do not globally override Spectre selectors or restyle package
  components to make the site look more bespoke.
- Custom CSS is an exception requiring Bradley Potts's explicit approval. It
  must address a concrete site-only need that no published Spectre API can
  express, remain minimal and narrowly scoped, use published tokens, and state
  the exception and reason in the handoff.
- If the missing capability is reusable or visual-system behavior, request it
  upstream through the process below and wait for a published package version;
  do not bridge the gap with temporary local styling.
- When touching existing custom CSS, remove or reduce it wherever the current
  published packages provide an equivalent. Do not expand legacy CSS merely
  because it already exists.
- Review every visual diff for package fidelity. Validation passing is not
  enough if a change duplicates, overrides, or visually diverges from the
  published Spectre packages.
- Brand direction in `BRAND.md` is expressed through Spectre's published
  themes and APIs. No site-level brand layer exists yet; adding one (named
  site custom properties for PHCDevworks identity) needs Bradley Potts's
  explicit approval first.

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

## Source of Truth

| Layer | Path | Rule |
| --- | --- | --- |
| Validation authority | `package.json` scripts | Docs must describe these scripts, not invent others |
| Site source | `src/pages/` · `src/layouts/` | Composes published Spectre components; no local design system |
| Build config | `astro.config.ts` · `tsconfig.json` | Starter-owned boilerplate; change only with an explicit reason |
| App manifest | `spectre.manifest.json` | Mirrors `package.json` `@phcdevworks/*` dependencies |
| Brand direction | `BRAND.md` | Expressed through Spectre, never as a parallel visual system |
| Public documentation | `README.md` · `CHANGELOG.md` · `TODO.md` · `ROADMAP.md` | Must match established behavior, not invent it |

## Human Approval Boundaries

These require explicit approval from Bradley Potts before the change is
committed:

- adding a site-level brand layer or any site-authored CSS
- changing the primary accent, secondary color, or primary typeface named in
  `BRAND.md`
- adding a hosting adapter, deploy script, or other production configuration
- adding a dependency outside the published `@phcdevworks/*` packages and the
  starter toolchain
- deployment, release, and tag actions

## Verification

`npm run check` is the standard validation gate — it runs `npm run build` then
`npm run manifest:validate`. Run it before any handoff when practical.

- Check for broken internal links in repository Markdown before finishing.
- State whether a rendered-page review is still needed for the touched pages.
- Keep changes easy to review and grounded in the current repo structure.
- Use `.codex/release-checklist.md` before production release or final release
  handoff.

`astro check` is not part of the gate yet: `@astrojs/check` does not support
the TypeScript 7 release the starter ships with. Restoring a typecheck step is
tracked in [TODO.md](TODO.md).

## Standard Handoff

Every AI-prepared change should report:

- files changed
- validation performed
- validation skipped, if any
- Spectre fidelity impact (components used, any local markup or CSS added or
  removed)
- company-first positioning impact for public copy changes
- remaining risk, including anything only a rendered-page review can catch

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

## Confidential External Identities

Never record external customer, vendor, user, client-site, or private-project
identities in tracked files, git metadata, reviews, releases, issues, or
handoffs. Use anonymous role-based wording such as "a downstream integration"
or "a production consumer." Public package and platform names are allowed
only when technically required to identify a dependency or supported
integration.

**Zero tolerance, no exceptions.** This is not a case-by-case judgment call.
Every upstream vendor, customer, client, or third-party identity — regardless
of how well-known, already public, or seemingly harmless — is forbidden from
appearing in any file, commit, tag, branch name, PR, issue, roadmap, TODO, or
agent output anywhere in this repo. If a vendor name is already present
anywhere in tracked files, it must be anonymized on sight, not left in place
because it predates this rule.

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
  delivered without `npm run check` (build + manifest validation) passing, and never let
  a self-expanded phase drift the site toward single-product Spectre framing
  — this repository represents PHCDevworks company-first (see Positioning
  above).
- Surface any new TODO request or roadmap expansion in the handoff for Bradley
  Potts in the same change it was made, and reflect cross-repo-relevant
  changes in the project-team's own ROADMAP.md/TODO.md.

## Pull Request Creation

Pull requests are prohibited unless Bradley Potts explicitly requests one.
The guidance below applies only to that explicit exception.

For an explicitly requested PR, populate every section of the repo's PR
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
- [GROK.md](GROK.md) — Grok (and Grok Bot) development scope and git authority
- [.github/copilot-instructions.md](.github/copilot-instructions.md) — Copilot
  IDE-facing scope and repository conventions
