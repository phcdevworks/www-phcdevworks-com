# Contributing to the PHCDevworks Website

Thanks for contributing to `www-phcdevworks-com`.

## Principles

- Keep changes focused and easy to review.
- Match current PHCDevworks and Spectre naming.
- Keep the site framed as the PHCDevworks company website, not a
  single-product Spectre site.
- Update repository docs when scripts, workflow, or ownership language changes.
- Prefer project-level configuration over machine-wide changes.
- Follow `BRAND.md` for visual identity decisions.

## Local Workflow

1. Install dependencies with `npm install`.
2. Start the local server with `npm run dev`.
3. Run `npm run check` (build plus manifest validation) before handing off
   when practical.
4. Use `npm run preview` to serve the production build locally.

## Troubleshooting

- **Build errors after pulling** — run `npm install` to sync dependencies before
  building; `node_modules/` and `dist/` are not committed.
- **Manifest validation fails** — keep the `www-phcdevworks-com` entry's
  `dependencies` in `spectre.manifest.json` in sync with the `@phcdevworks/*`
  dependencies in `package.json`.
- **TypeScript errors in `.astro` files** — confirm your editor uses the Astro
  VS Code extension. `astro check` is not part of the gate yet (see
  `TODO.md`).

## Spectre-First

Build pages from published `spectre-ui-astro` components and shipped `sp-*`
classes before writing any local markup or CSS. If Spectre does not provide
what a page needs, request it upstream rather than adding a local substitute.
Full order: "Spectre-First Building" in `AGENTS.md`.

## Pull Request Expectations

- Explain the intent of the change clearly.
- Keep documentation, config, and scripts in sync.
- Do not include unrelated formatting churn.
- Call out follow-up work if something is intentionally deferred.

## Scope Guidance

- Use this repository for the PHCDevworks public website and repo-level
  maintenance.
- Present Spectre as a major PHCDevworks platform within the broader company
  ecosystem.
- Do not introduce retired branding or outdated ownership language.
- Keep project settings cohesive with the Spectre documentation repository when
  the workflow is shared.

## AI Guidance Files

- `AGENTS.md` defines shared multi-agent boundaries for this repository.
- `CLAUDE.md` is the lead implementation guide.
- `CODEX.md` covers release readiness, production stabilization, and repo
  hygiene review.
- `COPILOT.md` defines repository-level Copilot support boundaries.
- `.github/copilot-instructions.md` keeps GitHub Copilot focused on support work
  inside the IDE.
- `JULES.md` defines automated micro-maintenance boundaries.
- `GROK.md` defines Grok (and Grok Bot) development-assistant scope and git
  authority.
