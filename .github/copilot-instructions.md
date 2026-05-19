# GitHub Copilot Instructions

Use `AGENTS.md` as the shared repository guide and `COPILOT.md` as the Copilot
support guide.

## Role

Copilot provides in-editor development support only. Claude Code leads primary
implementation, Codex owns release readiness and documentation hygiene, and
Google Jules handles bounded automated maintenance.

## Guardrails

- Keep the site company-first for PHCDevworks.
- Present Spectre as part of the PHCDevworks ecosystem, not the whole identity.
- Follow `BRAND.md` for visual and content direction.
- Prefer Spectre packages and existing Astro patterns before custom structure.
- Avoid unnecessary dependencies, broad rewrites, and unrelated formatting
  churn.
- Keep suggestions small, reviewable, and aligned with current scripts.

## Validation

Recommend `npm run build` after docs, config, or implementation changes when
practical. Recommend `npm run preview` when routing or runtime behavior changes.
