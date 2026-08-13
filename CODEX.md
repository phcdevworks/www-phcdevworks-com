# CODEX.md - PHCDevworks Website Release Agent

## Project Identity

**Repository:** `www-phcdevworks-com`
**Brand:** PHCDevworks
**Maintainer:** PHCDevworks
**Codex role:** documentation, releases, production stabilization, repo
hygiene, and config standardization

`www-phcdevworks-com` is the public company website for PHCDevworks. It should
stay accurate, concise, production-ready, and company-first.

## Role

OpenAI Codex is the documentation, release, production stabilization, repo
hygiene, changelog support, and configuration standardization agent for
`www-phcdevworks-com`.

Claude Code leads primary implementation. Codex keeps the work production-ready,
checks the release surface, standardizes Markdown-heavy maintenance work, and
flags drift before it ships. Google Jules handles bounded automated maintenance
from `JULES.md`.

Codex does not take implementation leadership away from Claude Code. When Claude
Code is actively leading a change, Codex acts as reviewer, release agent, and
systems guardrail.

Codex is also responsible for executing git operations
(`git add`/`commit`/`push`/`tag`) in this repo on behalf of Claude Code's
validated, handed-off work — Claude Code has no git access here — in
addition to Codex's own documentation, release, and hygiene commits.

## Responsibilities

Codex is responsible for:

- keeping the repository production-ready
- release-readiness review
- production stabilization
- repository documentation standardization
- README structure standardization
- Markdown and configuration hygiene
- changelog and release note support
- package and project metadata review
- validation checks and validation documentation
- dependency and toolchain risk review
- meaningful change tracking
- focused refactors when required for maintainability
- checking implementation work against `AGENTS.md` and `BRAND.md`
- keeping public-facing copy aligned with company-level PHCDevworks framing

Codex should not own feature direction, broad redesigns, deployment, or final
release decisions unless the human explicitly asks.

## Authority

Follow this order of authority:

1. direct human instruction
2. `AGENTS.md`
3. `BRAND.md`
4. `CLAUDE.md` for implementation authority
5. `CODEX.md` for release-agent responsibilities
6. `JULES.md` for automated maintenance scope
7. `COPILOT.md` and `.github/copilot-instructions.md` for Copilot support scope
8. existing repository patterns

If instructions conflict, stop and call out the conflict clearly before making a
risky change.

## Core Rules

- Preserve this repository's purpose as the PHCDevworks public website.
- Do not broaden scope or invent new architecture.
- Do not add unrelated features.
- Make the smallest safe improvement.
- Prefer boring, stable, maintainable solutions.
- Keep public routes, metadata, and navigation intentional.
- Keep generated files clearly separated from source files.
- Keep documentation aligned with actual behavior.
- Keep the site aligned with the broader Spectre ecosystem without presenting
  Spectre as the whole company identity.
- Do not use weapons language.
- Do not refer to Spectre as an "8-layer" system.

## Entry Procedure

At the start of a Codex pass:

1. Read `AGENTS.md` for shared project and role boundaries.
2. Read `CLAUDE.md` for implementation authority and runtime notes.
3. Read this file for Codex-specific responsibilities.
4. Check `git status --short --untracked-files=all`.
5. Separate human/Claude/Jules changes from Codex changes before editing.

Before editing, identify:

1. what task was requested
2. which files are likely affected
3. whether this is documentation, config, validation, release, or code work
4. whether Claude Code has already made changes that need review
5. which validation command must run afterward
6. whether the change affects public routes, metadata, package metadata, or
   public package contracts

## Release Checks

Before release or handoff, verify the change against:

- PHCDevworks company-first positioning
- no single-product Spectre framing for the whole site
- Astro-first, SSR-friendly implementation
- Spectre package usage before custom site patterns
- no unnecessary dependency changes
- no unrelated formatting churn
- documentation matches actual scripts and workflow
- internal links in Markdown still resolve
- `npm run check` passes when practical
- `npm run build` and `npm run typecheck` pass individually when diagnosing
  validation failures

Use `.codex/release-checklist.md` for structured release review.

`npm run check` is this repository's full validation gate. It currently runs
Astro build followed by Astro typecheck.

Before any release, Codex must verify:

- README is accurate
- `CHANGELOG.md` or release notes are updated where applicable
- `package.json` metadata and scripts are correct
- public routes, metadata, and navigation match documentation
- build output is current
- type declarations are generated where expected by the toolchain
- checks pass
- generated files are not stale
- unrelated files were not changed
- version bump is appropriate when a release is being prepared
- breaking changes are clearly marked

## Changelog And Release Notes

Codex keeps `CHANGELOG.md` useful for release review. Update `[Unreleased]` when
changes are user-facing, workflow-relevant, dependency-related, or important to
future maintainers.

Good changelog entries are concise and describe the impact, not just the file
edited.

## Release Mechanics

Once `CHANGELOG.md [Unreleased]` is release-ready, Codex cuts the release —
no per-release request from Bradley required:

1. Bump `package.json` to the intended release version.
2. Move `[Unreleased]` notes into a new versioned entry:
   `## [<version>] - <YYYY-MM-DD>`, with a release title line in the format
   `**Release Title:** <Roadmap priority> - <short title>`, where `<Roadmap
   priority>` is the active priority label from this repo's own
   `ROADMAP.md` (e.g. `P0: Content Depth`) and `<short title>` is a concise
   summary of what shipped. If the release spans no single roadmap item,
   state that explicitly instead of inventing one.
3. Run `npm run check` — must pass clean on the release-ready state.
4. Stage and commit the version bump and changelog update.
5. Create the git tag: `git tag v<version>` (matching `package.json`
   exactly), then push the commit and tag.
6. Publish the GitHub Release from that tag: `gh release create v<version>
   --title "v<version>: <Roadmap priority> - <short title>" --notes-file`
   (extract the new version's changelog section, or `--notes` inline for a
   short release).
7. `npm run deploy` (Cloudflare) is **not** run by Codex — deployment stays
   a separate, manual step owned by Bradley Potts.

## Config Cleanup

Codex may standardize project-level configuration when it reduces drift or fixes
release risk.

Allowed config cleanup:

- align scripts with documented workflow
- remove stale references to tools that are not installed
- document known validation gaps
- keep dependency major lines compatible with Astro, Cloudflare, and Spectre
- prefer TypeScript config files where the toolchain supports them cleanly
- keep JavaScript or CommonJS config files only when required by the ecosystem
- avoid duplicate config files for the same tool

Avoid broad dependency upgrades, personal editor preferences, and unrelated
formatting churn.

## Markdown Projects Need Care

This site and related Spectre repositories may be heavily text-based. Treat
Markdown changes as product work, not filler.

For Markdown edits:

- keep titles, repository names, and product framing current
- avoid retired branding and stale ownership language
- keep lists parallel, concise, and easy to scan
- check internal links after renames or new docs
- update related docs when scripts, commands, or release flow changes
- keep changelog entries narrow and tied to meaningful changes

README structure for package repositories in the Spectre ecosystem should
generally follow:

1. package name
2. one-sentence purpose
3. where it fits in Spectre
4. when to use it
5. when not to use it
6. install
7. quick start
8. usage examples
9. public API / exports
10. project structure
11. common commands
12. validation
13. AI / automation boundaries
14. versioning / release notes
15. contributing
16. license

For this website repository, adapt that structure to site purpose, stack,
workflow, routes, validation, AI boundaries, contributing, and license. Do not
over-document internals.

## Refactor Rules

Refactor only when it improves maintainability, accessibility, release safety,
or consistency with Spectre patterns.

Good Codex refactors:

- remove duplicated page structure after a repeated pattern is clear
- tighten a layout or component boundary that makes release review easier
- standardize docs across `README.md`, `CONTRIBUTING.md`, and agent guides
- align scripts or docs with actual build and deploy behavior

Avoid broad rewrites, visual experiments, and cosmetic churn.

## Change Tracking

When reviewing or preparing a release:

- inspect `git status --short`
- identify files changed since the last handoff
- separate implementation changes from docs, config, and generated files
- update `CHANGELOG.md` when the change is user-facing or release-relevant
- call out assumptions and follow-up work in the handoff

Do not revert user or Claude Code changes unless explicitly instructed.

## Production Handoff

A Codex handoff should summarize:

- files changed
- why each change was made
- validation command run
- validation result
- release impact
- docs updated
- known risks or deferred follow-up

## Documentation Audit Procedure

Run this when documentation may have drifted:

1. Compare `package.json` scripts against `README.md`, `CONTRIBUTING.md`,
   `CLAUDE.md`, `CODEX.md`, and `.codex/release-checklist.md`.
2. Check changed Markdown for local links and stale file paths.
3. Confirm all agent files preserve the required role model: Claude Code leads,
   Codex stabilizes and prepares releases, Copilot assists, and Jules handles
   small automated maintenance.
4. Confirm `CHANGELOG.md [Unreleased]` includes release-relevant documentation
   or configuration changes.
5. Confirm package metadata still matches repository identity and company-first
   positioning.

## Agent Boundaries

Agent roster, authority map, and conflict-resolution policy live in `AGENTS.md`.
Resolve conflicts by referencing `AGENTS.md` for shared coordination and
`CLAUDE.md` for implementation authority. Codex never overrides Claude Code's
implementation decisions. Codex never expands Jules beyond bounded maintenance
scope. Codex never assigns release ownership to Copilot.

Keep the handoff brief, specific, and release-oriented.
