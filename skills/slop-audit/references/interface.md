# Interface tells

Slop in an interface is rarely one ugly element. It is a cluster of choices made by reflex: the same fonts, the same chrome, the same emphasis, the same motion. Read each entry as a question about the work, not a banned ingredient.

The source audit at the end records what happened to every entry supplied for this skill.

## Type and emphasis

### Tag and emphasis inflation

**Looks like:** pill tags above every heading, italicized words in every paragraph, bold phrases mid-sentence, colored keywords, uppercase labels. The tags usually repeat the heading instead of adding metadata.

**Why it reads as slop:** emphasis is a scarce signal. When everything is emphasized, nothing is. The block looks like a template filling each slot rather than a writer deciding what matters.

**Evidence to collect:** count the emphasis devices in one block. Three or more in a single heading or paragraph is a trigger. Tags that restate the heading are decoration. Italics on ordinary words are a trigger.

**Fix:** one emphasis channel per block. Keep tags only for metadata a user filters or scans by. Use italics for titles or genuine asides. Bold the lede, not every proper noun. Delete the rest.

**Verdict:** valid, conditional on density. A single italic word or one tag can be correct.

### Reflex type

**Looks like:** Instrument Serif italic for one word in a sans headline, Space Grotesk for the UI, Bricolage Grotesque for a "playful" brand. Often paired with a warm cream ground, a terracotta accent, and negative tracking.

**Why it reads as slop:** these faces became the costume of AI landing pages. The problem is not the face. It is choosing it without a reason, then adding every other piece of the costume. The serif-italic accent word as the only typographic idea is the clearest tell.

**Evidence to collect:** font imports or files; whether the face comes from the brand or the first suggestion; display tracking below about `-0.04em`; the same face on a project whose content gives no reason for it.

**Fix:** pick the face from the content, audience, or existing brand. If the project already has a face, use it. If not, choose one family and one weight strategy, then write down why. Keep display tracking mild, around `-0.01em` to `-0.03em` at large sizes. Do not ban these fonts. Flag the cluster and the missing rationale.

**Verdict:** conditional. Instrument Serif, Space Grotesk, and Bricolage Grotesque are legitimate faces. Overuse and unconsidered pairing are the tell.

### Monospace overuse

**Looks like:** monospace on labels, navigation, buttons, captions, and body copy. Mono used as a texture to signal "technical".

**Why it reads as slop:** monospace slows reading and adds visual noise when it is not carrying code or aligned data. It is a shortcut to a mood.

**Evidence to collect:** mono on non-code text; more than one mono role; body copy set in mono; mono labels beside sans labels with no system.

**Fix:** reserve mono for code, IDs, hashes, timestamps, and tabular data. Use the body face for labels and UI. Keep at most one mono role.

**Verdict:** valid.

### Caps as texture

**Looks like:** all-caps subheads, all-caps buttons, all-caps labels, tracked out across the page.

**Why it reads as slop:** caps reduce word-shape recognition, so long caps strings are harder to read. Used everywhere, they flatten hierarchy instead of creating it.

**Evidence to collect:** caps on headings longer than a few words; caps without positive tracking; caps as the only difference between levels.

**Fix:** sentence case for headings. Caps only for short labels of two or three words, with positive tracking. Let size and weight carry hierarchy.

**Verdict:** conditional. Short uppercase labels are a normal convention.

### Type scale sprawl

**Looks like:** six or more sizes, three or four weights, `text-[13.5px]` one-offs, every section inventing a size. The smallest text is 11px or below.

**Why it reads as slop:** no scale means no hierarchy. Tiny type hides content and fails contrast and mobile reading. Arbitrary values make the page look almost systematic without being systematic.

**Evidence to collect:** unique font sizes in the view; smallest size; hard-coded values off the project's scale; number of weights.

**Fix:** one scale with four or five roles: display, heading, body, small, caption. Body at 16px, UI at 14px, captions at 12px to 13px, rarely below 12px. Use the project's tokens.

**Verdict:** conditional heuristic. "More than four sizes" is a trigger to look, not a law. The real test is whether each size has a distinct role.

### Extreme negative tracking

**Looks like:** `letter-spacing: -0.06em` on a display headline, letters touching, word shapes collapsing.

**Why it reads as slop:** tight tracking can be a display choice, but extreme values read as a font-size trick. They make the headline harder to parse and often collide at small viewports.

**Evidence to collect:** tracking below about `-0.04em`; collisions between letters; negative tracking carried into body text.

**Fix:** mild negative tracking for large display only, around `-0.01em` to `-0.03em`. Zero at body sizes. Positive tracking for small caps labels.

**Verdict:** conditional. Negative kerning itself is normal for display type. The extreme value and the lack of a reason are the tell.

### Meta-string rhythm

**Looks like:** "Design · Build · Ship", "EST. 2024 · LONDON · INDEPENDENT", middle dots between every pair of words.

**Why it reads as slop:** the pattern is a template device that adds rhythm without information. It reads as fake editorial metadata.

**Evidence to collect:** middle dots in headings or hero copy; separators between items that are not a list; credentials that mean nothing to the reader.

**Fix:** use middle dots only for compact metadata where space is tight, such as a footer line. In headings, write a sentence. Remove fake credentials.

**Verdict:** conditional. Middle dots are a legitimate separator for short metadata.

### Eyebrow and numbering chrome

**Looks like:** `01 / FOUNDATION` above a heading, a small uppercase caption above every section, breadcrumbs on a single-level page, section numbers that nothing references.

**Why it reads as slop:** it manufactures structure. When every section is numbered, the numbers carry no information. The eyebrow is often a label that repeats the heading in weaker words.

**Evidence to collect:** eyebrows above most headings; numbering that is never referenced; breadcrumbs that do not correspond to navigation; captions that restate the heading.

**Fix:** delete the eyebrow. Use numbering only when order matters or the numbers are referenced, as in documentation, steps, or legal text. Let the heading do the work.

**Verdict:** valid.

### Hero scale

**Looks like:** a headline at 12vw that fills the viewport, one word per line, body copy squeezed below the fold.

**Why it reads as slop:** size is used as a substitute for message. It pushes the actual content off-screen and breaks on small viewports.

**Evidence to collect:** display size relative to the viewport; line count; whether the headline clips; the body size left for the reader.

**Fix:** cap display type so the headline fits in two or three lines at the target viewport, and keep body copy readable. Use `clamp()` with a sane maximum. Let the message, not the point size, carry the hero.

**Verdict:** conditional. Large type is a valid art direction when it still serves the content.

## Composition and chrome

### Effect stacking

**Looks like:** a card with a border, a shadow, a translucent overlay, an inner card with another border, a divider between every row, and a gradient wash.

**Why it reads as slop:** each effect is a bid for depth. Together they fight. The eye sees chrome before content. It is the visual equivalent of piling on adjectives.

**Evidence to collect:** count independent depth and decoration devices on one surface. Nested bordered containers. More than one shadow layer. Dividers between every item. An overlay that has no layering job.

**Fix:** one primary depth device per surface. A border for containment and a subtle shadow for elevation can coexist when they do different jobs. Remove the inner container when it only repeats the outer one. Use space, not dividers, to group. Keep overlays for modals and real layering.

**Verdict:** valid.

### Accent rails

**Looks like:** a 3px to 4px colored vertical bar on the left edge of every card.

**Why it reads as slop:** the rail implies status or category but usually encodes nothing. Repeated on every card, it becomes noise.

**Evidence to collect:** rails on all cards; color not mapped to a state; a rail plus a border plus a shadow on the same card.

**Fix:** keep the rail only when color encodes status, category, or priority, and document the mapping. Otherwise remove it and use spacing or a label.

**Verdict:** conditional. A rail that encodes state is legitimate.

### Concentric radius

**Looks like:** outer card at `rounded-2xl`, inner button at `rounded-2xl`, padding of 8px. The corners fight even though the values match.

**Why it reads as slop:** nested curves that do not share a center look wrong before the viewer can name why. It is a craft defect rather than a moral one.

**Evidence to collect:** outer radius, inner radius, and the gap between them. The target is `outer = inner + padding`.

**Fix:** set the outer radius from the inner radius plus the gap. Use the project's radius scale.

**Verdict:** valid, covered by `better-ui`.

### Border weight consistency

**Looks like:** 1px borders next to 2px dividers, 0.5px hairlines next to 1px, icons with mixed stroke widths.

**Why it reads as slop:** mixed weights read as accidental. The eye picks up the inconsistency before it can name it.

**Evidence to collect:** border widths per role; divider weights; icon stroke widths; focus ring weight.

**Fix:** one border weight per role: surface, divider, focus. Pick 1px or a hairline for the density and display, then use it everywhere. Do not mix.

**Verdict:** partly invalid as stated. "Use 0.5px where 1px is used" is not a rule. A 0.5px line can disappear on non-retina displays. Keep the consistency test. Drop the prescription.

### Color-value sprawl

**Looks like:** a dozen near-identical grays, five accent opacities, arbitrary hex values, `rgba()` one-offs.

**Why it reads as slop:** near-duplicates create a surface that looks almost systematic but is not. It reads as generated variation rather than a palette.

**Evidence to collect:** count unique color values and opacity variants. Compare them with the project's tokens.

**Fix:** define roles: ground, ink, muted, line, accent. Use tokens. Three neutrals plus one accent is enough for most views. Use the opacity scale instead of one-off alpha values.

**Verdict:** valid.

### Gradient and glow

**Looks like:** a purple-blue gradient hero, a glow behind cards, glassmorphism on every surface, gradient text.

**Why it reads as slop:** it is the default "modern" skin. It adds no information and often hurts contrast.

**Evidence to collect:** gradients not tied to a brand or content; purple or multicolor defaults; glow used as the primary affordance; glass effects without a real layer beneath.

**Fix:** flat surfaces with one accent, or a gradient with a real job such as data encoding or a brand field. Remove glow unless it communicates state.

**Verdict:** valid, narrow. Covered by `baseline-ui`.

### Chart and diagram density

**Looks like:** a dashboard chart with eight series, gridlines, dual axes, annotations, a legend, and a gradient fill. A diagram with every node and every arrow.

**Why it reads as slop:** detail is used as a proxy for rigor. A chart with more marks than questions makes the reader work harder, not smarter.

**Evidence to collect:** number of series, axes, annotations, and labels; whether each mark supports the one question the chart answers; legends that repeat direct labels.

**Fix:** one question per chart. Drop series, gridlines, and annotations that do not serve it. Label directly instead of using a legend. For diagrams, show the path the reader needs, not the whole system.

**Verdict:** conditional. Density is fine in analytical tools when the reader asked for it.

## Copy

### Voice inflation

**Looks like:** "Let's build something weird", invented verbs, cutesy empty states, fake candor, every button a joke.

**Why it reads as slop:** it performs personality instead of communicating. It dates quickly and gets in the way of the task.

**Evidence to collect:** jokes in error states; slang that does not match the audience; a metaphor where a label belongs; nouns turned into verbs; a voice that performs personality instead of stating the task.

**Fix:** plain, specific, calm. Match the register of the task. Keep one human touch where it helps, not on every line. For prose mechanics, use `unslop`.

**Verdict:** conditional. The general writing patterns belong in `unslop`. The product-voice tell belongs here.

### Explainer padding

**Looks like:** a paragraph under every feature, helper text that restates the label, "Why this matters" sections, three sentences where one would do.

**Why it reads as slop:** it assumes the reader needs persuading at every step. It buries the action and reads as generated filler.

**Evidence to collect:** helper text that repeats the label; feature descriptions longer than the feature; paragraphs with no new fact, instruction, or constraint.

**Fix:** delete the sentence if it adds no fact, instruction, or constraint. Let labels and examples carry the meaning. For prose, use `unslop`.

**Verdict:** duplicate, conditional on context.

### Emoji and verbiage

**Looks like:** emojis in body copy, decorative emojis in headings, three adjectives where one would do, sentences that restate the previous sentence.

**Verdict:** duplicate. This belongs to `unslop`, which already covers decorative emojis, puffery, filler, and dense prose. Do not re-implement those rules here.

## Motion

### Motion everywhere

**Looks like:** every section fades and slides on scroll, long ease-in, elements that animate on load, hover on everything.

**Why it reads as slop:** motion without frequency or purpose reads as a demo reel. It slows repeat use and can make people motion-sick.

**Evidence to collect:** scroll-triggered animation count; durations; easing; `prefers-reduced-motion` handling; keyboard-triggered animations.

**Fix:** animate only when it explains a change, gives feedback, or preserves spatial continuity. Keep UI motion under 300ms, use ease-out on enter, and honor reduced motion. For the full bar, use `review-animations`.

**Verdict:** duplicate. Covered by `review-animations`, `animation-polish`, and `baseline-ui`.

## Source audit

### Web and visual entries

| Original entry | Verdict | Disposition |
| --- | --- | --- |
| Tags and italics everywhere | Valid, conditional | Merged into tag and emphasis inflation |
| Instrument Serif, Space Grotesk, Bricolage Grotesque | Conditional | Reflex type. Flag the cluster, not the font |
| Overuse of monospace fonts | Valid | Monospace overuse |
| Dividers, layered shadows, translucent overlays, bordered containers | Valid | Effect stacking |
| Charts made ridiculously detailed | Conditional | Chart and diagram density |
| Overly colloquial copy, invented words, Apple-site voice | Conditional, partly duplicate | Voice inflation. Prose mechanics stay in `unslop` |
| Code breadcrumbs, section numbering, captions above headings | Valid | Eyebrow and numbering chrome |
| Purple gradients | Valid, narrow | Gradient and glow. Covered by `baseline-ui` |
| ALL CAPS subheadings | Conditional | Caps as texture |
| Middle dots as separators | Conditional | Meta-string rhythm |
| Emojis in body text, useless verbiage | Duplicate | Deferred to `unslop` |
| Hero fonts absurdly oversized | Conditional | Hero scale |
| Explanatory descriptive text | Duplicate, conditional | Explainer padding. Prose stays in `unslop` |
| Nested elements without concentric corners | Valid, duplicate | Concentric radius. Covered by `better-ui` |
| Inconsistent line and border weights, 1px where 0.5px should be | Partly invalid | Kept consistency. Rejected the 0.5px prescription |
| Excessive scroll animations and jarring easing | Duplicate | Deferred to `review-animations` and `animation-polish` |
| More than four font sizes, smallest under 12px | Conditional heuristic | Type scale sprawl |
| Colorful vertical lines on card edges | Conditional | Accent rails |
| Dropdown buttons with dropdown icons | Invalid as stated | Rejected as a general rule. A chevron is an affordance. Flag only redundant chevrons on non-menu controls |

### Design indicator entries

| Original entry | Verdict | Disposition |
| --- | --- | --- |
| Tags | Duplicate | Tag and emphasis inflation |
| Italicized words | Duplicate | Tag and emphasis inflation |
| Instrument Serif, negative kerning | Conditional | Reflex type and extreme negative tracking |
| Over the top detailed UI | Duplicate | Effect stacking |
| Dividers | Duplicate | Effect stacking |
| Multiple color shades and opacities | Valid | Color-value sprawl |
| Containers with borders | Duplicate | Effect stacking |
| Diagrams, the more detailed the worse | Duplicate | Chart and diagram density |
| Code breadcrumbs | Duplicate | Eyebrow and numbering chrome |
| Section numbering | Duplicate | Eyebrow and numbering chrome |
| Eyebrow text | Duplicate | Eyebrow and numbering chrome |
