# www-phcdevworks-com Agent Guide

## Project Identity

- Repository: `www-phcdevworks-com`
- Brand: PHCDevworks
- Maintainer: PHCDevworks
- Scope: public company website, supporting content, and project-level website
  configuration

## Mission

Build and maintain the flagship public website for PHCDevworks.

This repository represents the company first. It may showcase Spectre and other
PHCDevworks initiatives prominently, but it must not be framed as a
single-product website.

The site should feel modern, technical, premium, restrained, and deliberate.

## Core Positioning

This repository represents:

- PHCDevworks as the parent company and operating brand
- the broader PHCDevworks ecosystem
- products, systems, and technical initiatives under that umbrella
- Spectre as a major platform within that story, not the entire story

## Working Principles

- Keep naming consistent with PHCDevworks and current company positioning.
- Treat this site as a downstream Spectre application where appropriate.
- Reuse Spectre packages and patterns where appropriate instead of inventing a
  parallel design system.
- Prefer clarity, maintainability, and strong structure over novelty.
- Keep project-level configuration aligned with the actual site workflow.
- Do not carry forward retired branding, old organization names, or narrow
  single-product framing.
- Favor small, reviewable changes over broad rewrites.
- Keep Astro-first, SSR-friendly, and maintainable.
- Do not add unnecessary dependencies.
- Do not rewrite unrelated files.

## Content Standards

- Keep contributor-facing Markdown concise and accurate.
- Make repository docs match the actual scripts and workflow.
- Keep public-facing messaging company-first, technically credible, and concise.
- Do not describe this repository as the Spectre website alone.
- Present Spectre as part of the PHCDevworks ecosystem, not the sole identity of
  the site.
- Avoid vague marketing filler, bloated copy, startup clichés, and
  over-claiming.

## Configuration Standards

- Preserve project-level settings only.
- Favor shared editor behavior over personal theme, font, or UI preferences.
- Keep line endings, indentation, and save behavior aligned with
  `.editorconfig`, `.gitattributes`, and local workspace settings.
- Do not introduce unnecessary dependencies or unrelated configuration churn.

## Verification

- Run `npm run build` after documentation or config changes when practical.
- Check for broken internal links in repository Markdown before finishing.
- Keep changes easy to review and grounded in the current repo structure.

## Visual Brand Guardrails

The site must follow a strict visual identity.

### Brand Character

The visual language should feel:

- modern
- technical
- premium
- restrained
- high-contrast
- system-driven
- deliberate

It should not feel:

- playful
- soft
- generic SaaS
- corporate stock-photo driven
- pastel
- gradient-heavy
- visually noisy

### Color Rules

Primary brand accent:

- `#E6004F`

Use a dark-first palette built around:

- black / near-black backgrounds
- white / off-white primary text
- neutral grays for borders, dividers, and muted text
- `#E6004F` as the primary accent

Rules:

- do not introduce blue as a brand color
- do not use multicolor gradients
- do not rotate accent colors by page
- use the accent color selectively for emphasis, active states, accent bars, and
  primary calls to action
- never change the primary accent from `#E6004F` unless explicitly instructed

### Typography Rules

Typography is a core part of the brand.

Rules:

- use one primary sans-serif family across the site
- keep headings bold and high-impact
- keep hierarchy strong and obvious
- do not swap fonts casually
- do not use soft or playful display fonts
- do not rely on decorative typography tricks
- never change the site’s primary font without explicit instruction

The site should feel typography-first, not image-first.

### Background and Texture Rules

Approved:

- black or near-black backgrounds
- subtle engineering-style grid treatments
- restrained texture or depth
- minimal visual noise

Not approved:

- blue gradients
- glowing startup blobs
- decorative illustrations
- stock photography
- generic abstract hero art

### Surface and Glass Rules

Glassmorphism may be used lightly and intentionally.

Allowed:

- subtle translucent dark panels
- restrained blur on navigation, cards, or callout areas
- low-contrast layering that supports hierarchy
- premium modern surface treatment that improves structure

Not allowed:

- heavy blur across the page
- bright frosted-glass effects
- flashy futuristic gimmicks
- anything that reduces readability or makes the site feel trendy instead of
  precise

Glass effects should support structure, not become the brand by themselves.

### Layout Rules

The site should use:

- strong alignment
- clean spacing rhythm
- asymmetrical balance where useful
- generous negative space
- structure-led composition

Avoid:

- cluttered sections
- over-stacked cards
- template-like sameness
- decorative filler used to compensate for weak layout

### Signature Motifs

The brand may reuse these motifs:

- accent bars or underline rules
- subtle technical grid backgrounds
- selective accent emphasis inside headings
- thin borders and structured dividers

These motifs should be used consistently and sparingly.

## Design System Rules

This site should use Spectre as its implementation foundation where appropriate.

- align with upstream Spectre direction where possible
- reuse Spectre packages and patterns instead of inventing a parallel system
- keep site-specific composition in this repository
- do not create a disconnected local design language

This repository owns company presentation, page composition, site structure, and
public-facing messaging. It does not own upstream token meaning or reusable
styling contracts that belong in Spectre packages.

## Repo Ownership

This repository owns:

- company website information architecture
- page composition and route structure
- homepage and public-facing marketing pages
- site-specific content sections and messaging
- navigation, footer, calls to action, and supporting pages
- company-level presentation of products, platforms, and ecosystem initiatives

This repository does not own:

- upstream token definitions
- a separate visual language disconnected from Spectre
- generic marketing fluff
- decorative imagery used to compensate for weak layout or copy

## Working Priorities

1. homepage structure and messaging
2. reusable layout foundation
3. header and footer
4. ecosystem and product visibility
5. clear calls to action
6. responsive polish
7. accessibility
8. metadata and SEO
9. performance and maintainability

## Execution Style

Prefer one meaningful improvement at a time.

Examples of good pull requests:

- add base layout
- add site header and footer
- create homepage hero and section structure
- improve CTA clarity
- add metadata
- tighten copy on a single page
- improve accessibility in one focused area

Examples of bad pull requests:

- redesign everything at once
- add random dependencies
- mix unrelated cleanup into one diff
- introduce off-brand visual experiments
- add imagery that breaks the typography-first direction
- replace the dark technical visual language with generic SaaS styling

## Pull Request Expectations

Each pull request should:

- stay narrowly scoped
- explain what changed
- explain why it matters
- list files changed
- note assumptions if any
- recommend the next logical follow-up

## Definition of Done

A change is done when:

- it keeps the site aligned with PHCDevworks company positioning
- it respects the typography-first, image-free design direction
- it maintains the dark, high-contrast visual identity with `#E6004F` as the
  primary accent
- it avoids unnecessary drift from Spectre
- it improves clarity, structure, accessibility, performance, or maintainability
- the diff is easy to review

## Default Decision Rule

When in doubt:

- choose clarity over cleverness
- choose hierarchy over decoration
- choose restraint over visual noise
- choose maintainability over novelty
- choose company-level framing over single-product framing
