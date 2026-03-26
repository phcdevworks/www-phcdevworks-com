# Spectre Website Agent Guide

## Project Identity

- Repository: `www-phcdevworks-com`
- Product: Spectre
- Maintainer: PHCDevworks
- Scope: public website, repository docs, and project-level configuration

## Working Principles

- Keep naming consistent with Spectre and PHCDevworks.
- Prefer clear maintainability over novelty in project configuration.
- Keep repository-level configuration aligned with the documentation repository
  where the workflow is shared.
- Do not carry forward retired branding or organization names.

## Content Standards

- Keep contributor-facing Markdown concise and accurate.
- Make repository docs match the actual scripts and project workflow.
- Use the website repository to describe public-facing ownership as Spectre run
  by PHCDevworks.

## Configuration Standards

- Preserve project-level settings only.
- Favor shared editor behavior over personal theme, font, or UI preferences.
- Keep line endings, indentation, and save behavior aligned with
  `.editorconfig`, `.gitattributes`, and the local workspace settings.

## Verification

- Run `npm run build` after documentation or config changes when practical.
- Check for broken internal links in repository Markdown before finishing.
