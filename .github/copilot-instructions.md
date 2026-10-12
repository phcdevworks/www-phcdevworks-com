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

Copilot provides in-editor development support. Claude Code leads primary
implementation, Codex owns release readiness and documentation hygiene, and
Google Jules handles bounded automated maintenance. Copilot has commit,
push, and tag authority per the companywide grant — see `AGENTS.md`.

xAI Grok (including Grok Bot) works under these same instructions, with
`GROK.md` taking precedence on git authority.

## Guardrails

- Keep the site company-first for PHCDevworks.
- Present Spectre as part of the PHCDevworks ecosystem, not the whole identity.
- Follow `BRAND.md` for visual and content direction.
- Follow existing code patterns and package boundaries.
- Prefer Spectre packages and existing Astro patterns before custom structure.
- Use Spectre tokens or Spectre UI recipes instead of local visual primitives.
- Avoid unnecessary dependencies, broad rewrites, and unrelated formatting
  churn.
- Keep `spectre.manifest.json` in sync with `@phcdevworks/*` dependencies in
  `package.json`.
- Keep suggestions small, reviewable, and aligned with current scripts.
- Update docs and tests when public behavior changes.
- Do not own release decisions.

## Spectre-First Building

Before choosing, importing, or adding any `@phcdevworks` package, read
`node_modules/@phcdevworks/spectre-manifest/spectre.manifest.json` and import
only the exports listed there. Then work through this order before adding
markup structure, a wrapper component, or CSS:

1. Semantic HTML and Astro output appropriate to the content.
2. An existing `spectre-ui-astro` component and its public props, slots, and
   variants.
3. Shipped `sp-*` classes and `spectre-ui` recipe functions.
4. An existing layout, component, or pattern in this repo.
5. Otherwise, stop and flag the gap for an upstream request — do not build a
   local substitute.

Default to zero new site-authored CSS. Full rules: "Spectre-First Building" and
"Strict Spectre UI Astro Guardrails" in [AGENTS.md](../AGENTS.md).

## Validation

Recommend `npm run check` (production build plus manifest validation) as the
full validation command when practical. Recommend `npm run build` or
`npm run manifest:validate` individually when diagnosing failures. Recommend
`npm run preview` when routing or page output changes.
