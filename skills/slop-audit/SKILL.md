---
name: slop-audit
description: Audit interfaces and codebases for AI slop, the reflexive type, decoration, copy, and architecture choices that make generated work look generated. Use when asked for an anti-slop pass, when a page or repo "feels AI-generated" or overdesigned, or when reviewing a design or diff specifically for slop tells. Not a general design or code review.
---

# Slop audit

A slop audit finds the places where a choice was made by default rather than by the work. One tell is a data point. A cluster in the same view is a pattern. The output is evidence and a fix, not a verdict on taste.

## Branches

- **Interface**: type, emphasis, color, composition, motion, product copy. See [references/interface.md](references/interface.md).
- **Codebase**: coupling, structure, state, boundaries. See [references/codebase.md](references/codebase.md).
- **Both**, when the request spans design and code. Run the interface pass first, then the codebase pass.

## Process

1. **Scope and collect evidence.**
   Name the surface under review. Walk it once without judging. Record a file and line, a selector, a component name, or a screenshot region for every candidate. Completion: every candidate has a location.

2. **Name the tell.**
   Use the catalog. A tell is a pattern, not a single element: "three 12px uppercase eyebrows above three headings" beats "uses uppercase". Completion: every candidate maps to a named tell or is set aside as taste.

3. **Triage.**
   Mark each finding High, Medium, or Low.
   - **High**: it blocks comprehension, trust, or change. Examples: unreadable contrast, a state the type system permits but the domain forbids, a change that touches six files.
   - **Medium**: it reads generated and costs clarity, but the page or code still works.
   - **Low**: polish. Fix only when the surface is otherwise sound.

   Kill false positives here. A font, color, border, chevron, or animation is not slop on its own. Repetition, lack of a job, and mismatch with the content decide.

4. **Report.**
   Use one table: `Location | Tell | Evidence | Fix`. Group by branch, then severity, highest first. Each row names one fix. Omit taste. If a suspected tell survives triage, say why it stays: "kept: the accent bar encodes status."

5. **Fix only when asked.**
   Apply fixes in the project's existing system: its tokens, components, type scale, and folder conventions. Do not introduce a second styling or architecture approach to remove slop. When a fix crosses into prose, use `unslop`. When it crosses into craft values, use `better-ui`, `better-typography`, or `baseline-ui`. When it crosses into motion, use `review-animations` or `animation-polish`. When it crosses into module shape, use `codebase-design`. Report applied fixes as Before/After rows, following the craft skill you used.

6. **Re-audit.**
   Re-run the catalog on the changed surface. A tell is closed when the evidence is gone, not when the row is marked done. Completion: every reported tell is fixed, explicitly deferred, or reclassified with a reason.

## High-signal tells

### Interface

- **Emphasis inflation**: pills, italics, bold, caps, and colored words competing in one block.
- **Reflex type**: Instrument Serif italic, Space Grotesk, or Bricolage Grotesque chosen because they look "designed", often with a warm cream ground and a serif-italic accent word.
- **Effect stacking**: a bordered card inside a bordered card, with a shadow, a translucent overlay, and a divider.
- **Eyebrow and numbering chrome**: `01 / FOUNDATION`, small caps above every heading, breadcrumbs that no one navigates.
- **Decoration with no job**: purple gradients, glow, colorful left rails, middle-dot rhythm strings, charts with more marks than questions.
- **Type scale sprawl**: six sizes, three weights, and 11px captions.
- **Motion everywhere**: every section fades up on scroll, easing that starts slow, exits that fight the enter.

### Codebase

- **Implicit coupling**: a change in one module breaks another without an interface change.
- **Layer-first folders**: `controllers/`, `services/`, `repositories/` mirror the framework, so every feature is scattered across all three.
- **Duplication that must stay in sync**: the same rule in the UI, the API, and the database.
- **Representable illegal states**: booleans that can contradict, optional fields that must travel together, stringly-typed status.
- **God files and shotgun surgery**: one file with many reasons to change, or one change that edits many files.
- **Pass-through wrappers**: a layer that adds no behaviour.
- **Validation away from the boundary**: unparsed input travels deep, and every layer guards it again.

## False positives

Reject these unless repetition or context makes them a tell:

- A chevron on a dropdown. It is an affordance, not slop.
- A single italic word or one accent color used for emphasis.
- A border, a shadow, or a hairline used once for a real grouping.
- A serif, grotesque, or monospace face used for the job it was drawn for.
- Section numbers in documentation where the numbers are referenced.
- A large hero headline that fits the viewport and carries the message.
- Duplication that is cheaper than a wrong abstraction.
- Layer-first folders in a small app with one feature.

## What this skill is not

Not a style police. Not a ban list. Not a replacement for `unslop` (prose), `better-ui` and `better-typography` (craft values), `review-animations` (motion), or `codebase-design` (module shape). It is the audit lens that decides which of those to reach for.
