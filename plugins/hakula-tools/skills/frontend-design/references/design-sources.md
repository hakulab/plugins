# Design Sources

This file holds the full rule set behind [`SKILL.md`](../SKILL.md), including rules `SKILL.md` does not condense, with each rule's source, strength, and any disagreement between sources. Project conventions and user-stated rules without a public source live only in `SKILL.md`. A rule's strength is one of:

| Strength        | Meaning                                                                |
| --------------- | ---------------------------------------------------------------------- |
| WCAG A, AA, AAA | A normative success criterion.                                         |
| Multi-system    | At least two of Apple, Material, Carbon, and GOV.UK agree.             |
| Research        | An NN/g study or review.                                               |
| System          | One design system's rule.                                              |
| Platform        | A W3C Community Group report or a browser vendor's published guidance. |
| Practitioner    | A respected book or author, without the force of a standard.           |

A rule with several sources takes the strength of its strongest one.

## Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Foundations](#foundations)
  - [Design tokens](#design-tokens)
  - [Spacing scale](#spacing-scale)
  - [Type scale](#type-scale)
  - [Interaction states](#interaction-states)
- [Layout and spacing](#layout-and-spacing)
  - [Visual hierarchy](#visual-hierarchy)
  - [Grouping and separation](#grouping-and-separation)
  - [Key lines](#key-lines)
  - [Text alignment](#text-alignment)
  - [Small screens first](#small-screens-first)
  - [Reflow and zoom](#reflow-and-zoom)
  - [Images and loading](#images-and-loading)
- [Typography](#typography)
  - [Typefaces](#typefaces)
  - [Measure](#measure)
  - [Leading](#leading)
  - [Text spacing overrides](#text-spacing-overrides)
  - [Case](#case)
- [Color](#color)
  - [Color roles](#color-roles)
  - [Dark mode default](#dark-mode-default)
  - [Text contrast](#text-contrast)
  - [Non-text contrast](#non-text-contrast)
  - [Color is never the only cue](#color-is-never-the-only-cue)
  - [Text on colored backgrounds](#text-on-colored-backgrounds)
- [Data display](#data-display)
  - [Tables](#tables)
  - [Numeric columns](#numeric-columns)
  - [Chart type](#chart-type)
  - [Data-ink](#data-ink)
  - [Proportional encoding](#proportional-encoding)
  - [Direct labels](#direct-labels)
  - [Categorical colors](#categorical-colors)
- [Forms and feedback](#forms-and-feedback)
  - [Form layout](#form-layout)
  - [Labels](#labels)
  - [Validation](#validation)
  - [Error messages](#error-messages)
  - [Primary button](#primary-button)
  - [Action wording](#action-wording)
  - [Loading feedback](#loading-feedback)
  - [Empty states](#empty-states)
- [Accessibility](#accessibility)
  - [Keyboard operation](#keyboard-operation)
  - [Focus](#focus)
  - [Target size](#target-size)
  - [Dragging alternatives](#dragging-alternatives)
  - [Headings and widget patterns](#headings-and-widget-patterns)
  - [Text alternatives](#text-alternatives)
- [Motion](#motion)
  - [Durations](#durations)
  - [Purpose](#purpose)
  - [User control](#user-control)
- [Slides and diagrams](#slides-and-diagrams)
  - [One idea per slide](#one-idea-per-slide)
  - [Story structure](#story-structure)
  - [Diagram hierarchy and labels](#diagram-hierarchy-and-labels)
- [Choosing the sources](#choosing-the-sources)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Foundations

### Design tokens

- **Rule:** Define tokens for color, type, space, radius, and shadow, and reference them at call sites. Choose a small set of colors, two weights, and a few sizes before building.
- **Why:** Tokens are the single source of truth across design tools and code, and they make theming possible. Fewer choices produce consistency without policing every screen.
- **Source:** [DTCG format 2025.10](https://www.designtokens.org/tr/2025.10/format/), [Carbon color tokens](https://carbondesignsystem.com/elements/color/overview/), [Refactoring UI, limit your choices](https://www.refactoringui.com/).
- **Strength:** Platform.

### Spacing scale

- **Rule:** Use one spacing scale and stay on it. Carbon builds on multiples of 2, 4, and 8 from an 8px mini unit, GOV.UK uses a 5px-based scale from 0 to 60px, and Material uses 4dp and 8dp. Keep GOV.UK's 5px spacing and Carbon's 8px grid in separate artifacts.
- **Why:** Arbitrary margins destroy rhythm and make small changes expensive. Because the systems disagree on base units, consistency is the shared rule.
- **Source:** [Carbon spacing](https://carbondesignsystem.com/elements/spacing/overview/), [GOV.UK spacing](https://design-system.service.gov.uk/styles/spacing/).
- **Strength:** Multi-system.

### Type scale

- **Rule:** Use a small fixed type scale, map every size to a role, and set body text at the scale's body role. GOV.UK runs 16 to 80px in named steps, Carbon runs 12 to 92px from a single equation, and Material 3 has 15 baseline roles plus 15 emphasized roles. GOV.UK uses 19px body with 25px leading, Carbon's dense product scale starts at 14px, and WCAG sets no minimum font size. Take the type scale, body size, and spacing scale from the same system.
- **Why:** Ad hoc sizes create inconsistent hierarchy, and small body text is the first thing to fail under zoom, low vision, and projection.
- **Source:** [GOV.UK type scale](https://design-system.service.gov.uk/styles/type-scale/), [Carbon typography](https://carbondesignsystem.com/elements/typography/overview/), [Material 3 type scale](https://m3.material.io/styles/typography/type-scale-tokens).
- **Strength:** Multi-system.

### Interaction states

- **Rule:** Define every interaction state, covering enabled, hover, focus, pressed, and disabled. Material's state layers use 8% hover, 10% focus, 10% pressed, and 16% drag opacity.
- **Why:** Undefined states get invented per component.
- **Source:** [Material 3 states](https://m3.material.io/foundations/interaction/states/state-layers).
- **Strength:** System.

## Layout and spacing

### Visual hierarchy

- **Rule:** Give each view one dominant element, rank everything else as secondary or tertiary, and make the focal point obvious at a glance. Build hierarchy with size, weight, and color together, using two or three text colors and about two weights for UI hierarchy.
- **Why:** Attention is scarce, an undifferentiated field gives the eye no entry point, and size alone produces a flat, crowded hierarchy.
- **Source:** [Duarte, slide design](https://www.duarte.com/blog/perfect-your-slide-design/), [Refactoring UI](https://www.refactoringui.com/), [Refactoring UI, 7 practical tips](https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886).
- **Strength:** Practitioner.

### Grouping and separation

- **Rule:** Use proximity to encode grouping, and give important elements more surrounding space. Separate with space, background, or shadow before adding a border.
- **Why:** Nearness reads as relationship, and extra space reads as importance.
- **Source:** [Carbon spacing](https://carbondesignsystem.com/elements/spacing/overview/), [Refactoring UI](https://www.refactoringui.com/).
- **Strength:** System.

### Key lines

- **Rule:** Align to a grid and to shared key lines. Place type against the padding edge, and keep text out of the padding.
- **Why:** Alignment removes visual noise and makes scanning easier.
- **Source:** [Carbon 2x grid](https://carbondesignsystem.com/elements/2x-grid/overview/).
- **Strength:** System.

### Text alignment

- **Rule:** Left-align body copy and center only short headings. Do not center whole text blocks, and do not justify body text in the browser without hyphenation.
- **Why:** Centered and justified blocks have ragged or uneven edges that slow reading and break alignment with other elements.
- **Source:** [Butterick, centered text](https://practicaltypography.com/centered-text.html), [Butterick, justified text](https://practicaltypography.com/justified-text.html).
- **Strength:** Practitioner.

### Small screens first

- **Rule:** Design small-screen first, starting with a single column.
- **Why:** The constrained layout exposes the real content order, and enhancement is easier than reduction.
- **Source:** [GOV.UK layout](https://design-system.service.gov.uk/styles/layout/), [web.dev, responsive basics](https://web.dev/articles/responsive-web-design-basics).
- **Strength:** System.

### Reflow and zoom

- **Rule:** Support 200% text resize, and reflow at 320 CSS px (400% zoom) without two-dimensional scrolling, except for parts that need two-dimensional layout such as data tables, maps, and diagrams. Set the viewport meta tag to `width=device-width, initial-scale=1`, and do not block zoom. Avoid `maximum-scale` and `user-scalable=no`.
- **Why:** Zooming must not force horizontal back-and-forth reading, and without the viewport tag, mobile browsers render a desktop width and shrink it.
- **Source:** [WCAG 1.4.4](https://www.w3.org/WAI/WCAG22/Understanding/resize-text.html), [1.4.10](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html), [web.dev, responsive basics](https://web.dev/articles/responsive-web-design-basics).
- **Strength:** WCAG AA.

### Images and loading

- **Rule:** Give images `max-width: 100%` and explicit `width` and `height`. Meet Core Web Vitals at the 75th percentile: LCP at or under 2.5s, INP at or under 200ms, and CLS at or under 0.1.
- **Why:** Oversized images cause horizontal scrolling, missing dimensions cause layout shift, and these metrics measure loading, interactivity, and visual stability as users experience them.
- **Source:** [web.dev, responsive basics](https://web.dev/articles/responsive-web-design-basics), [web.dev, Web Vitals](https://web.dev/articles/vitals).
- **Strength:** Platform.

## Typography

### Typefaces

- **Rule:** Use at most two typefaces, each with a fixed role. Put decorative faces in headers or illustrations, and keep body copy in a text face.
- **Why:** More faces compete and muddy the hierarchy.
- **Source:** [Butterick, mixing fonts](https://practicaltypography.com/mixing-fonts.html), [NN/g, pairing typefaces](https://www.nngroup.com/articles/pairing-typefaces/).
- **Strength:** Practitioner.
- **Disagreement:** Butterick says any two identifiably different fonts can mix, including two serifs, and that mixing is never required. Common web advice pairs serif with sans and avoids similar classifications, while NN/g favors a single family with multiple weights.

### Measure

- **Rule:** Fill the available width up to 90 characters.
- **Why:** Long lines make the eye travel far and lose its place, while a narrow column wastes the available width.
- **Source:** [Butterick, line length](https://practicaltypography.com/line-length.html), [Every Layout, axioms](https://every-layout.dev/rudiments/axioms/).
- **Strength:** Practitioner.
- **Disagreement:** 45 to 75 characters (Every Layout, citing _The Elements of Typographic Style_) versus 45 to 90 (Butterick). GOV.UK says no more than 75.

### Leading

- **Rule:** Set body leading around 1.3 to 1.5, and never below 1.2. Butterick gives 120 to 145% of point size, GOV.UK body is 19px with 25px leading (about 1.32), and WCAG's override test requires the layout to survive 1.5.
- **Why:** Tight leading merges lines and makes tracking hard.
- **Source:** [Butterick, line spacing](https://practicaltypography.com/line-spacing.html), [WCAG 1.4.12](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html).
- **Strength:** Practitioner.

### Text spacing overrides

- **Rule:** Do not break when users override text spacing. The layout must survive 1.5 line-height, 2em paragraph spacing, 0.12em letter spacing, and 0.16em word spacing.
- **Why:** Users with dyslexia or low vision may apply these overrides.
- **Source:** [WCAG 1.4.12](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html).
- **Strength:** WCAG AA.

### Case

- **Rule:** Use sentence case for body text, headings, and most UI labels. All caps is acceptable for short labels, captions, and overlines, provided the text is tracked and kerned and the label is genuinely short. Do not use caps for paragraphs or multi-line headings, and avoid all-lowercase headings and titles, which are less scannable than mixed case. Apply caps with `text-transform: uppercase` so the underlying text keeps its case and screen readers announce the original word.
- **Why:** Capitals homogenize word shapes and slow reading at body sizes, so they need extra tracking to stay legible.
- **Source:** [Butterick, all caps](https://practicaltypography.com/all-caps.html), [NN/g, 113 guidelines](https://www.nngroup.com/articles/113-design-guidelines-homepage-usability/), [NN/g, glanceable fonts](https://www.nngroup.com/articles/glanceable-fonts/), [Stanford UIT](https://uit.stanford.edu/accessibility/learn-about/typography/all-caps).
- **Strength:** Research.
- **Disagreement:** NN/g's general guidance says use sparingly or not at all, while its glanceable-reading study says uppercase can be faster for isolated short words.

## Color

### Color roles

- **Rule:** Use role-based color tokens, and build light and dark themes from the same role set. Map `primary`, `on-primary`, `surface`, `container`, and `outline` to components, and keep raw hex values at the token definition. In dark themes, make each added layer lighter, as Carbon's near-black surfaces do from Gray 100 (`#161616`).
- **Why:** Roles keep light and dark themes and their contrast pairs coherent.
- **Source:** [Material 3 color roles](https://m3.material.io/styles/color/roles), [Carbon color](https://carbondesignsystem.com/elements/color/overview/).
- **Strength:** Multi-system.

### Dark mode default

- **Rule:** Offer dark mode, follow the OS setting, and keep light mode the default for a general audience. NN/g found light mode tends to produce better visual performance for normal-vision users, while some low-vision users benefit from dark.
- **Why:** The evidence favors light mode by default, and user choice covers the exceptions.
- **Source:** [NN/g, dark mode](https://www.nngroup.com/articles/dark-mode/).
- **Strength:** Research.

### Text contrast

- **Rule:** Set text contrast to at least 4.5:1, and large text to at least 3:1, where large means 18pt (about 24px) or 14pt bold (about 18.5px). Do not round a computed 4.499:1 up to a pass.
- **Why:** Low-contrast text is unreadable for people with low vision or impaired contrast perception.
- **Source:** [WCAG 1.4.3](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html).
- **Strength:** WCAG AA.
- **Disagreement:** Datawrapper gives minimum ratios of 2.5:1 for large text and 4:1 for small text, while WCAG 1.4.3 requires 4.5:1 for normal text and 3:1 for large text. Follow WCAG.

### Non-text contrast

- **Rule:** Keep UI component boundaries, states, meaningful graphics, and focus indicators at least 3:1 against adjacent colors.
- **Why:** Otherwise, the control or its state disappears for low-vision users.
- **Source:** [WCAG 1.4.11](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).
- **Strength:** WCAG AA.

### Color is never the only cue

- **Rule:** Never use color as the only cue. Add text, an icon, a shape, or a pattern.
- **Why:** Color blindness and monochrome displays remove the meaning.
- **Source:** [WCAG 1.4.1](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html).
- **Strength:** WCAG A.

### Text on colored backgrounds

- **Rule:** For secondary text on a colored background, use white at reduced opacity or a color of the background's hue, and stay within [Text contrast](#text-contrast).
- **Why:** Grey on a colored background looks washed out, while a color of the background's hue lowers the text's emphasis and keeps it vivid.
- **Source:** [Refactoring UI](https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886).
- **Strength:** Practitioner.

## Data display

### Tables

- **Rule:** Use a table when the task is comparing values across rows and columns. Put a human-readable identifier in the first column, so each row is recognizable. Never show an auto-generated ID there.
- **Why:** Tables scale and support comparison better than cards.
- **Source:** [NN/g, data tables](https://www.nngroup.com/articles/data-tables/).
- **Strength:** Research.

### Numeric columns

- **Rule:** Right-align numeric columns, use tabular figures (`font-variant-numeric: tabular-nums lining-nums`) so digits share a width, and put units in the header. Give the table a caption and use scoped headers.
- **Why:** Aligned digits make columns comparable, and captions and scopes make tables navigable.
- **Source:** [Butterick, grids of numbers](https://practicaltypography.com/grids-of-numbers.html), [Butterick, alternate figures](https://practicaltypography.com/alternate-figures.html), [GOV.UK table](https://design-system.service.gov.uk/components/table/), [Web Typography, numerals and tables](https://book.webtypography.net/Web-Typography_Numerals-and-tables.pdf).
- **Strength:** System.

### Chart type

- **Rule:** Choose the chart type from the message: line for change over time, bar for comparison and shares, scatter for correlation, and histogram for distribution.
- **Why:** The statement the chart must make determines its form.
- **Source:** [Datawrapper, chart types](https://www.datawrapper.de/blog/chart-types-guide), [FT Visual Vocabulary](https://github.com/Financial-Times/chart-doctor/tree/main/visual-vocabulary).
- **Strength:** Practitioner.

### Data-ink

- **Rule:** Maximize data-ink by removing gridlines, background fills, 3D effects, and decoration that do not carry data.
- **Why:** Non-data ink competes with the data for attention.
- **Source:** [Tufte's data-ink, summarized by EU DataViz](https://data.europa.eu/apps/data-visualisation-guide/chart-junk-and-data-ink-origins), [Nature](https://www.nature.com/documents/Nature_scientific_illustration_author_guide.pdf).
- **Strength:** Practitioner.

### Proportional encoding

- **Rule:** Keep the visual encoding proportional to the values. Do not truncate the axis on bar charts or use area and volume to exaggerate differences, and treat dual axes with care.
- **Why:** Distorted encoding misleads readers about magnitude.
- **Source:** [Tufte's lie factor, summarized by EU DataViz](https://data.europa.eu/apps/data-visualisation-guide/chart-junk-and-data-ink-origins), [Datawrapper, chart colors](https://academy.datawrapper.de/article/113-what-to-consider-when-choosing-colors-for-data-visualization), [FT Visual Vocabulary](https://github.com/Financial-Times/chart-doctor/tree/main/visual-vocabulary).
- **Strength:** Practitioner.

### Direct labels

- **Rule:** Label series directly, explain every encoding, and add a short description with the key takeaway.
- **Why:** Readers should not have to hunt through a legend.
- **Source:** [Datawrapper, chart colors](https://academy.datawrapper.de/article/113-what-to-consider-when-choosing-colors-for-data-visualization).
- **Strength:** Practitioner.

### Categorical colors

- **Rule:** Keep categorical chart colors to about seven, use grey for context, and test for color-vision deficiency.
- **Why:** More colors force legend-hunting and become indistinguishable.
- **Source:** [Datawrapper, chart colors](https://academy.datawrapper.de/article/113-what-to-consider-when-choosing-colors-for-data-visualization).
- **Strength:** Practitioner.

## Forms and feedback

### Form layout

- **Rule:** Use a single-column form with one question per row, though short related fields such as city, state, and postal code may share a row.
- **Why:** Multiple columns interrupt the vertical reading flow.
- **Source:** [NN/g, web form design](https://www.nngroup.com/articles/web-form-design/).
- **Strength:** Research.

### Labels

- **Rule:** Give every input a persistent visible label, preferably above the field. Placeholders may add hints, but they must not replace labels.
- **Why:** Disappearing hints strain memory and make error recovery harder.
- **Source:** [WCAG 3.3.2](https://www.w3.org/WAI/WCAG22/Understanding/labels-or-instructions.html), [NN/g, placeholders](https://www.nngroup.com/articles/form-design-placeholders/), [NN/g, form white space](https://www.nngroup.com/articles/form-design-white-space/).
- **Strength:** WCAG A.

### Validation

- **Rule:** Validate only on submit, accept flexible formats, and turn off native HTML5 validation if it conflicts with your accessible error pattern.
- **Why:** Early validation punishes slow typists, and native HTML5 bubbles cannot be made consistent or reliably accessible.
- **Source:** [GOV.UK validation](https://design-system.service.gov.uk/patterns/validation/), [GOV.UK error message](https://design-system.service.gov.uk/components/error-message/).
- **Strength:** System.

### Error messages

- **Rule:** Name the field in an error message, say how to fix the error, and preserve what the user entered. Add an error summary at the top, move focus to it, and link each item to its field.
- **Why:** Users need to find and correct errors without re-entering data.
- **Source:** [WCAG 3.3.1](https://www.w3.org/WAI/WCAG22/Understanding/error-identification.html), [3.3.3](https://www.w3.org/WAI/WCAG22/Understanding/error-suggestion.html), [GOV.UK error message](https://design-system.service.gov.uk/components/error-message/), [GOV.UK error summary](https://design-system.service.gov.uk/components/error-summary/).
- **Strength:** WCAG AA.

### Primary button

- **Rule:** Use one primary button per page.
- **Why:** Several primary buttons reduce the impact of each and obscure the next step.
- **Source:** [GOV.UK button](https://design-system.service.gov.uk/components/button/).
- **Strength:** System.

### Action wording

- **Rule:** Use the same word for the same action across the flow, so if the button says "Publish", the confirmation says "Published". Name the action, and avoid vague text such as "Submit" or "Click here".
- **Why:** Inconsistent vocabulary forces users to re-learn each step, and vague button text hides what the action does.
- **Source:** [NN/g, heuristic 4](https://www.nngroup.com/articles/ten-usability-heuristics/), [GOV.UK button](https://design-system.service.gov.uk/components/button/).
- **Strength:** Research.

### Loading feedback

- **Rule:** Match feedback to the delay: under 1s needs none, over 1s needs a busy indicator, and over 10s needs progress and an estimate. Use skeletons for container loads and inline spinners for actions.
- **Why:** Users need to know whether the system is working.
- **Source:** [NN/g, response times](https://www.nngroup.com/articles/response-times-3-important-limits/), [Carbon loading](https://carbondesignsystem.com/patterns/loading-pattern/).
- **Strength:** Research.

### Empty states

- **Rule:** Design the empty state to explain what will appear here, why it is empty, and what to do next.
- **Why:** First-use and zero-result states are where users decide whether the product works.
- **Source:** [Carbon empty states](https://carbondesignsystem.com/patterns/empty-states-pattern/).
- **Strength:** System.

## Accessibility

### Keyboard operation

- **Rule:** Make all functionality keyboard-operable, with no per-keystroke timing requirement.
- **Why:** Blind users, switch users, and voice-input users depend on the keyboard interface.
- **Source:** [WCAG 2.1.1](https://www.w3.org/WAI/WCAG22/Understanding/keyboard.html).
- **Strength:** WCAG A.

### Focus

- **Rule:** Keep focus order meaningful, focus always visible, and the focused item at least partly unobscured. Never remove the focus indicator without a visible replacement, and for a strong indicator (WCAG AAA, 2.4.13), use at least a 2px perimeter with 3:1 contrast.
- **Why:** Sighted keyboard users cannot operate what they cannot see.
- **Source:** [WCAG 2.4.3](https://www.w3.org/WAI/WCAG22/Understanding/focus-order.html), [2.4.7](https://www.w3.org/WAI/WCAG22/Understanding/focus-visible.html), [2.4.11](https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html), [2.4.13](https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance.html).
- **Strength:** WCAG AA.

### Target size

- **Rule:** Make pointer targets at least 24 by 24 CSS pixels, or space them so a 24px circle centered on each does not intersect another. Prefer 44 by 44 for primary controls, which meets WCAG AAA and matches the Apple default for iOS and iPadOS.
- **Why:** Small, close targets cause mis-taps for people with tremor or limited dexterity.
- **Source:** [WCAG 2.5.8](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html), [2.5.5](https://www.w3.org/WAI/WCAG22/Understanding/target-size-enhanced.html), [Apple HIG accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility).
- **Strength:** WCAG AA.

### Dragging alternatives

- **Rule:** Give every dragging action a single-pointer alternative. Let a click on a slider track move the thumb, or provide a numeric input.
- **Why:** Some users cannot press and drag accurately.
- **Source:** [WCAG 2.5.7](https://www.w3.org/WAI/WCAG22/Understanding/dragging-movements.html).
- **Strength:** WCAG AA.

### Headings and widget patterns

- **Rule:** Write descriptive headings and labels, and follow APG patterns for widgets, giving menus, dialogs, tabs, and comboboxes their documented roles, states, and keyboard behavior.
- **Why:** Users navigate by headings and expect standard widget keys.
- **Source:** [WCAG 2.4.6](https://www.w3.org/WAI/WCAG22/Understanding/headings-and-labels.html), [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/).
- **Strength:** WCAG AA.

### Text alternatives

- **Rule:** Provide text alternatives for informative images. Give complex images such as charts and diagrams both a short description and a long description of the essential information. Render text as real text.
- **Why:** Assistive technology cannot recover meaning from pixels, and users cannot restyle an image.
- **Source:** [WCAG 1.1.1](https://www.w3.org/WAI/WCAG22/Understanding/non-text-content.html), [WAI complex images](https://www.w3.org/WAI/tutorials/images/complex/), [WCAG 1.4.5](https://www.w3.org/WAI/WCAG22/Understanding/images-of-text.html).
- **Strength:** WCAG AA.

## Motion

### Durations

- **Rule:** Keep UI effects at 150, 200, or 300ms and larger spatial transitions at 350, 500, or 750ms, following Material's Standard motion scheme converted to web curves.
- **Why:** Shorter durations feel instant, longer ones feel sluggish, and spatial moves need more time to read.
- **Source:** [Material 3 motion specs](https://m3.material.io/styles/motion/overview/specs).
- **Strength:** System.

### Purpose

- **Rule:** Use motion to show what changed or to direct attention, and remove decorative motion. No autoplaying parallax or scattered entrance effects.
- **Why:** Non-essential movement distracts.
- **Source:** [Reynolds, design tips](https://www.garrreynolds.com/design-tips).
- **Strength:** Practitioner.

### User control

- **Rule:** Give users control over motion. For non-essential content that starts automatically beside other content, provide a way to pause, stop, or hide moving, blinking, or scrolling content lasting more than five seconds, and provide the same controls or a frequency adjustment for auto-updating content (2.2.2). Also let users disable non-essential interaction-triggered motion, such as through `prefers-reduced-motion` (AAA, 2.3.3).
- **Why:** Moving and auto-updating content distracts people with attention or reading difficulties, and interaction-triggered motion can cause nausea, migraine, and dizziness for people with vestibular disorders.
- **Source:** [WCAG 2.2.2](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html), [2.3.3](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions.html).
- **Strength:** WCAG A.

## Slides and diagrams

### One idea per slide

- **Rule:** Put one idea on each slide and pass the three-second glance test. Make each slide read like a billboard with large type, whitespace, and images, since the best slides may have almost no text. Avoid bullet walls and slideuments.
- **Why:** Audiences cannot read dense slides while listening, so the spoken word carries the detail and the slide carries the point.
- **Source:** [Duarte, slide design](https://www.duarte.com/blog/perfect-your-slide-design/), [Duarte, one idea per slide](https://www.linkedin.com/posts/nancyduarte_this-mistake-is-costly-when-your-presentation-activity-7371184349502885888-n_yo), [Reynolds, design tips](https://www.garrreynolds.com/design-tips).
- **Strength:** Practitioner.

### Story structure

- **Rule:** Structure the talk as a story. Move from the status quo to what could be, alternate between the two, and end with a clear call to action.
- **Why:** Story creates the tension that makes an audience pay attention.
- **Source:** [Duarte, HBR](https://hbr.org/2012/10/structure-your-presentation-li).
- **Strength:** Practitioner.

### Diagram hierarchy and labels

- **Rule:** Give diagrams a visual hierarchy and complete labels. Make the most important elements the most saturated and detailed while keeping background elements neutral, label every element and the first instance of every object, organize with figure parts and subheadings, and use consistent arrows to carry meaning.
- **Why:** A diagram is an argument about relationships, and unlabeled elements make it ambiguous.
- **Source:** [Nature, scientific illustration guide](https://www.nature.com/documents/Nature_scientific_illustration_author_guide.pdf).
- **Strength:** Practitioner.

## Choosing the sources

WCAG, GOV.UK, and Carbon form the smallest set that covers the skill's surfaces without asking an agent to internalize a branded visual language. WCAG supplies the only rules that are both normative and mechanically checkable. GOV.UK supplies the best public evidence for the highest-risk web surface (data entry and error recovery), and Carbon supplies the patterns the other two lack for dense product screens and charts. Material 3 is the strongest alternative and the best source for color roles, state opacities, and motion tokens, but adopting it wholesale would impose an expressive identity and a large token vocabulary that the skill does not need.

- **[WCAG 2.2 AA plus WAI-ARIA APG](https://www.w3.org/WAI/WCAG22/Understanding/)**

  - **Covers:** Testable criteria for contrast, focus, targets, reflow, text spacing, motion, errors, labels, and alt text, plus widget roles and keyboard behavior. It applies across web pages, slides, and diagrams without prescribing visual language, layout, or content.
  - **Conflicts and costs:** None with visual systems, though as a floor it constrains every other choice.

- **[GOV.UK Design System](https://design-system.service.gov.uk/)**

  - **Covers:** Evidence-based patterns for forms, labels, validation, error summaries, buttons, tables, spacing, type scale, and service-page layout. It is strongest on transactional web forms and public-service content, and weak on dashboards, charts, and expressive marketing surfaces.
  - **Conflicts and costs:** Its austere visual language, 5px spacing scale, 19px body text, and GDS Transport typeface conflict with Carbon and Material values.

- **[IBM Carbon](https://carbondesignsystem.com/)**

  - **Covers:** Tokens, the 2x grid, spacing and type scales, color themes, interaction states, empty and loading patterns, data tables, and Carbon Charts. It is strongest on data-dense product UI, dashboards, and enterprise apps, and weaker on public-service form content and slides.
  - **Conflicts and costs:** IBM Plex and the 2x grid carry brand identity. Its 8px base unit and dense 14px body text conflict with GOV.UK.

- **[Material Design 3](https://m3.material.io/)**

  - **Covers:** The most complete visual system, offering 26 color roles, 30 type styles, state layers, motion durations, elevation, component states, and broad cross-platform app coverage. It is strong for Android and token-driven theming, though heavy for a small skill.
  - **Conflicts and costs:** Its expressive visual language and dynamic color fight a brief that wants a distinct identity, and its token surface costs context. Its values conflict with GOV.UK and Carbon.

- **[Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/accessibility)**

  - **Covers:** Platform conventions, control sizing, accessibility expectations, and interaction feel for Apple platforms. It is well suited to native Apple apps, though it does not standardize web pages, dashboards, or slides.
  - **Conflicts and costs:** It is bound to Apple platforms, and while its 44pt default target size overlaps WCAG AAA, it does not replace web semantics.

- **Practitioner canon** (Butterick, Every Layout, Refactoring UI, Duarte, Reynolds, Tufte, Datawrapper, NN/g, and Nature)

  - **Covers:** Visual craft such as measure, leading, font pairing, numerals, hierarchy, spacing, slide glance media, and data-ink, filling the aesthetic and editorial gaps the systems leave, especially for slides and diagrams.
  - **Conflicts and costs:** Single-author recommendations can disagree, as in a 45 to 75 character measure versus 45 to 90.

- **Platform guidance**

  - **Covers:** Viewport setup, responsive images, Core Web Vitals, and the design-token format, from W3C Community Groups and browser vendors.
  - **Conflicts and costs:** Vendor guidance reflects one browser's implementation, so check it against the others.
