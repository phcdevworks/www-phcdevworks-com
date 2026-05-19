# Codex Release Checklist

Use this checklist before a release, production deploy, or final handoff.

## Repository State

- [ ] `git status --short` reviewed
- [ ] unrelated local changes identified and left untouched
- [ ] generated files are either expected or absent
- [ ] dependency changes are intentional and explained

## Brand And Content

- [ ] PHCDevworks is framed as the company and parent brand
- [ ] Spectre is presented as part of the PHCDevworks ecosystem
- [ ] public copy avoids generic SaaS filler and over-claiming
- [ ] visual or content changes respect `BRAND.md`
- [ ] no retired branding or outdated organization names remain

## Documentation

- [ ] `README.md` matches current scripts and project scope
- [ ] `CONTRIBUTING.md` matches current workflow
- [ ] `CHANGELOG.md` is updated for release-relevant changes
- [ ] Markdown internal links resolve
- [ ] agent guidance remains consistent across `AGENTS.md`, `CLAUDE.md`,
      `CODEX.md`, `JULES.md`, `COPILOT.md`, and
      `.github/copilot-instructions.md`

## Build And Runtime

- [ ] `npm install` is not required unless dependencies changed
- [ ] `npm run build` passes when practical
- [ ] `npm run typecheck` passes when Astro, TypeScript, dependency, or config
      behavior changed
- [ ] `npm run preview` or local runtime check completed when page behavior
      changed
- [ ] new routes are reachable from intentional navigation surfaces
- [ ] metadata remains accurate for changed pages

## Accessibility And UX

- [ ] headings follow a clear hierarchy
- [ ] links and interactive elements have visible focus states
- [ ] text remains readable on mobile and desktop
- [ ] layouts avoid overlap and decorative noise
- [ ] motion and visual effects remain restrained

## Handoff

- [ ] changed files listed
- [ ] validation commands listed
- [ ] changelog/release-note impact described when relevant
- [ ] assumptions noted
- [ ] next follow-up recommended only when useful
