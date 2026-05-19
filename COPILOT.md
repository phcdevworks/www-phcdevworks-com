# COPILOT.md - PHCDevworks Website Support

## Role Summary

GitHub Copilot is the general development support assistant for
`www-phcdevworks-com`.

Copilot supports:

- inline code completion
- small code suggestions
- test suggestions
- TypeScript assistance
- API usage hints
- refactor suggestions
- pattern-aware implementation help
- developer productivity inside the IDE

Copilot does not own:

- lead implementation decisions
- architecture direction
- release coordination
- production stabilization ownership
- repo-wide AI governance
- automated maintenance workflows

## Authority Boundaries

- Claude Code is lead developer and primary implementation owner.
- OpenAI Codex owns documentation, releases, production stabilization, repo
  hygiene, and config standardization.
- Google Jules owns automated maintenance for small fixes, dependency updates,
  and micro-updates.
- Copilot provides support and does not override ownership decisions.

## Repository Guardrails

- Keep this site company-first for PHCDevworks, not single-product Spectre
  framing.
- Reuse Spectre packages and patterns before introducing custom alternatives.
- Keep changes Astro-first, SSR-friendly, and maintainable.
- Avoid unnecessary dependencies and unrelated formatting churn.
- Keep guidance aligned with `AGENTS.md`, `CLAUDE.md`, `CODEX.md`, `JULES.md`,
  and `BRAND.md`.

## Code Conventions

- Prefer strict, explicit TypeScript types and avoid `any`.
- Keep naming consistent with current PHCDevworks and Spectre conventions.
- Preserve existing route, layout, and style structure unless a task requires a
  targeted change.
- Keep refactors focused and small.

## Validation Expectations

- Run `npm run build` after docs, config, or implementation changes when
  practical.
- Recommend `npm run typecheck` when Astro or TypeScript behavior changes.
- Use `npm run preview` when runtime behavior needs Cloudflare validation.
- Keep docs and scripts synchronized when workflows change.

Primary operational prompts for Copilot live in
`.github/copilot-instructions.md`.
