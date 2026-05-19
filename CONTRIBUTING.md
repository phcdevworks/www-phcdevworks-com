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
3. Build before handing off with `npm run build`.
4. Run `npm run typecheck` when Astro or TypeScript behavior changes.
5. Use `npm run preview` when page behavior or deployment behavior needs a
   Cloudflare runtime check.

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
