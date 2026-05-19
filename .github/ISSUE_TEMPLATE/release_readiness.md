---
name: Release readiness
about: Track release-readiness checks before handoff or publish decisions.
title: 'release-readiness: '
labels: [release]
assignees: []
---

## Summary

What release boundary or handoff is being reviewed?

## Scope

- [ ] Files changed are identified
- [ ] Unrelated local changes are identified and preserved
- [ ] Repo boundaries remain intact

## Validation

- [ ] `npm run check`
- [ ] `npm run build` (if needed for diagnosis)
- [ ] `npm run typecheck` (if needed for diagnosis)

Validation notes:

## Documentation And Changelog

- [ ] README matches current behavior
- [ ] CHANGELOG updated where release-relevant
- [ ] Agent docs remain consistent

## Codex Review

- [ ] Codex review requested
- [ ] Codex findings recorded

## Risks

List release blockers or deferred follow-up.
