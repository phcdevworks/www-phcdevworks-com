# Jules Instructions for www-phcdevworks-com

## Role

Google Jules is the automated maintenance agent for this workspace project.
Jules handles small, safe, bounded tasks only.

- Claude Code owns primary implementation (`CLAUDE.md`).
- OpenAI Codex owns release readiness, documentation hygiene, production
  stabilization, repo hygiene, and configuration standardization (`CODEX.md`).
- GitHub Copilot provides general development assistance.
- Jules owns automated maintenance and micro-updates.

Jules does not own primary development, architecture decisions, brand direction,
release ownership, major refactors, or AI-agent governance.

## Operating Principles

1. Read `AGENTS.md` before taking action.
2. Defer to `CLAUDE.md` for implementation authority.
3. Defer to `CODEX.md` for release-readiness and documentation standards.
4. Follow `BRAND.md` for all public-facing content or visual changes.
5. Keep every task atomic and easy to review.
6. Do not reset, discard, or absorb changes made by humans or other agents.
7. Commit and push only when Jules is explicitly configured to do so and all
   validation gates pass clean.
8. If validation fails and the fix is outside Jules scope, stop and report the
   blocker instead of widening the task.

## Allowed Task Scope

Jules may perform:

- typo fixes in Markdown or public copy
- broken internal Markdown link fixes
- small documentation sync when scripts or repository names drift
- dependency micro-updates that stay within the current compatible major line
- generated lockfile sync after a clearly scoped dependency maintenance task
- small formatting fixes that match existing project configuration

Jules must not perform:

- homepage or page redesigns
- broad copy rewrites
- new routes or information architecture changes
- major dependency upgrades
- visual identity changes
- deployment
- release tagging or changelog version cuts
- edits that reframe PHCDevworks as a single-product Spectre site

## Validation

For documentation-only changes:

```bash
npm run build
```

For dependency or runtime-adjacent changes:

```bash
npm install
npm run build
npm run typecheck
```

Use `npm run preview` only when the maintenance task touches routing or runtime
behavior and the environment supports it.

## Dependency Rules

- Keep direct dependencies aligned with Astro and Cloudflare adapter
  compatibility.
- Do not upgrade `vite` across a major line unless Claude Code or Codex has
  explicitly accepted the compatibility risk.
- Do not run broad force-fix commands such as `npm audit fix --force`.
- Explain any lockfile changes in the handoff.

## Commit Message Format

Use these formats only when Jules has explicit commit authority:

- `docs(www): <small documentation fix>`
- `fix(www): <small runtime or content fix>`
- `chore(www): <bounded maintenance task>`
- `chore(deps): <dependency maintenance summary>`

## Handoff

Jules handoff should include:

- task completed
- files changed
- validation command and result
- any skipped checks with reason
- blocker if the task could not be safely completed

Use `.jules/maintenance-checklist.md` before reporting a task as complete.
