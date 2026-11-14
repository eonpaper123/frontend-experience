# Brand identity as one system

Use this reference for a new identity, a refresh, a critique, or any combination of logo, typography, and palette. It is not a landing-page style recipe. The goal is a coherent identity whose parts can be explained, checked, compared, and handed to implementation.

This guide is an independent synthesis informed by the MIT-licensed [Brand Identity skill](https://github.com/fatihaydost/brand-identity-skill). The repository license was checked on 2026-11-15. This repository does not redistribute that skill's scripts, templates, fonts, or generated assets.

## Start with one mechanism

Define each identity set with one sentence that can generate the mark, type choice, and palette together. Add one expressive move: the single part allowed to speak loudly. If the three parts need unrelated rationales, the set is a collage rather than a system.

Choose two to four decision axes that matter to the brief, such as technical to human, restrained to expressive, or institutional to conversational. Place every candidate set on those axes. Candidate sets should differ on at least two axes, while the parts within one set should sit on the same side of each axis.

Treat any retained logo, typeface, or color as a constraint. Adapt the new parts to it. If the retained part conflicts with the brief or accessibility, identify the conflict and its consequence; do not quietly replace it.

## Reject generic defaults

For every mark, typeface, and color decision, ask: **Would this same proposal plausibly be offered to another brand in this sector?**

- If yes, connect it to a concrete fact in the brief or change it.
- Words such as “warm,” “premium,” and “modern” are not enough on their own.
- Keep at least one candidate set free of the familiar defaults already common in the sector.
- Compare against the user's actual competitors rather than a generic industry moodboard.

This test is about distinctiveness, not novelty for its own sake. A familiar form is valid when it solves the brief, renders well, and is applied with an ownable mechanism.

## Separate measurement from judgement

Record conclusions with their evidence type:

- **Measured:** contrast, glyph coverage, file validity, small-size rendering, or a documented license result.
- **Judgement:** coherence, recognizability, tone, and competitive distinction.
- **Research evidence:** label the source and whether support is strong, limited, or practice-led.

Do not claim that a color converts or a typeface creates trust without product evidence. Automated gates can reject a broken file or contrast failure; they cannot select the best identity.

## Seven-step workflow

1. **Resolve only blocking inputs.** For logo, type, and palette, record `new`, `refresh`, `keep`, or `none`. Confirm languages, numeric content, available files or site, desired number of sets, audience, attributes, and relevant competitors. Reuse facts already present in the supplied product.
2. **Write the sets together.** Give every set its mechanism, axis positions, competitive difference, mark idea, display and text roles, and palette roles before polishing one set in isolation.
3. **Test marks in two focused rounds.** Build a contact sheet, inspect the marks at normal and small sizes, name one defect per mark, correct it, and inspect again. A further round should clear a specific gate or cliché rather than restart direction.
4. **Review the complete identity card.** Judge the mark, type, palette, representative copy, and product context together. Re-run only the part that failed a gate.
5. **Present comparable choices.** For each set, show the mechanism, competitor difference, logo, type, palette, and check results in the same structure. State a recommendation with reasons, then let the decision owner or an explicitly authorized delegate choose or request a deliberate mix.
6. **Build the selected kit.** Produce approved logo variants, typography rules, palette roles and tokens, clear-space and minimum-size rules, representative applications, and one or two misuse examples.
7. **Hand off by role.** Map palette roles and typography roles to design tokens. Preserve editable source files, export formats, font and asset licenses, and the evidence behind measured claims.

## Component contracts

### Mark and wordmark

- A mark should identify before it explains.
- Construct vector marks from filled geometry and deliberate boolean operations on a consistent grid, such as the source's 100-unit working grid, rather than text elements hidden inside the symbol.
- Inspect at 16 px and 32 px; provide a simplified small mark when detail collapses.
- A wordmark-only direction still needs an ownable wordmark detail and a designed small mark for favicon and compact contexts.
- Reference palette roles from the logo rather than embedding unrelated color values.
- Test monochrome, light, dark, and the actual background roles the product will use.

### Typography

- Display type carries voice; text type carries sustained reading.
- Pin variable-font axes deliberately, including optical size where supported.
- Verify every required language, numeral, punctuation, weight, and platform rendering path.
- Prefer redistributable fonts with clear licenses. For a commercial typeface, include its license boundary and a viable free alternative rather than bundling the font.

### Color

- Define color by hue, chroma, lightness, and ground, then assign functional roles.
- Keep brand roles separate from semantic success, warning, danger, and information colors.
- Measure actual foreground/background pairs in each relevant theme.
- When a main brand color lacks 3:1 contrast on a ground, treat it as ink or decoration on that ground rather than as a guaranteed UI-control color.
- Hand implementation named roles and tokens, not a loose page of hex values.

The source's additional numeric conventions are useful only when that construction method is selected: track wordmarks in 1/1000 em units, design the compact mark for roughly 16-48 px use, and treat a primary form below 3:1 against a ground as ground-specific ink rather than a general UI foreground. Measure the actual exported assets instead of copying these values without context.

## Observable acceptance

- Every set has one mechanism and one expressive move.
- Sets differ on at least two brief-specific axes; components within each set agree.
- Retained assets remain unchanged unless the user selected a refresh.
- Mark details survive the intended small sizes and required backgrounds.
- Type covers required languages and numeric content with documented licenses.
- Foreground/background contrast is measured on the actual role pairs.
- The comparison labels measured results and judgement separately.
- The selected kit includes tokens, source and export files, license notes, and misuse examples.
- No generated mockup, automated gate, or identity card is presented as market validation.

## Copyable task prompt

```text
Create [three] brand identity sets from this brief: [brief].
For logo, type, and palette, the states are [new/refresh/keep/none].
Required languages and numeric content: [requirements].
Existing assets and product surfaces: [links/files].
Relevant competitors: [list].

Give each set one mechanism, one expressive move, and positions on 2-4
brief-specific decision axes. Apply the sector-default test to every mark,
type, and color choice. Compare the sets in one consistent identity-card
format. Separate measured gates from design judgement, inspect marks at 16 px
and 32 px, verify font and asset licenses, and measure real contrast pairs.
Recommend one set with reasons, but wait for the decision owner or an explicitly
authorized delegate before making the final guidelines kit. After selection,
hand off named design tokens,
editable sources, exports, license notes, and 1-2 misuse examples.
```
