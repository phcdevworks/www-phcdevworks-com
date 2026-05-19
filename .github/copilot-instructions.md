# GitHub Copilot Instructions

Use `AGENTS.md` as the shared repository guide and `COPILOT.md` as the Copilot
support guide.

Before suggesting edits:

1. Read `AGENTS.md`.
2. Read `CLAUDE.md`.
3. Read `CODEX.md`.
4. Read `COPILOT.md`.
5. Read `package.json`.

## Role

Copilot provides in-editor development support only. Claude Code leads primary
implementation, Codex owns release readiness and documentation hygiene, and
Google Jules handles bounded automated maintenance.

## Guardrails

- Keep the site company-first for PHCDevworks.
- Present Spectre as part of the PHCDevworks ecosystem, not the whole identity.
- Follow `BRAND.md` for visual and content direction.
- Follow existing code patterns and package boundaries.
- Prefer Spectre packages and existing Astro patterns before custom structure.
- Use Spectre tokens or Spectre UI recipes instead of local visual primitives.
- Avoid unnecessary dependencies, broad rewrites, and unrelated formatting
  churn.
- Keep suggestions small, reviewable, and aligned with current scripts.
- Update docs and tests when public behavior changes.
- Do not own release decisions.

## Validation

Recommend `npm run check` as the full validation command when practical.
Recommend `npm run build` or `npm run typecheck` individually when diagnosing
failures. Recommend `npm run preview` when routing or runtime behavior changes.
