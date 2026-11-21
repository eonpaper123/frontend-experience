# Brand identity as one system

Use the context-led color section for every new or materially changed color direction. Use the full reference for a new identity, refresh, critique, or any combination of logo, typography, and palette. It is not a landing-page style recipe. The goal is a coherent identity whose parts can be explained, checked, compared, and handed to implementation.

This guide is an independent synthesis informed by the MIT-licensed [Brand Identity skill](https://github.com/fatihaydost/brand-identity-skill). The repository license was checked on 2026-11-15. This repository does not redistribute that skill's scripts, templates, fonts, or generated assets.

<a id="brand-color-system"></a>
## Establish a context-led brand color system before implementation

The goal is not to choose an attractive fallback when colors are unspecified. First establish why this product should use color in a particular way, then implement it. Existing briefs, brand guidelines, approved directions, design tokens, and real product surfaces are authoritative. User-retained colors and identity assets are constraints; do not recolor them because a new method or aesthetic preference is available. For a local correction, repair only the affected roles rather than reopening the identity.

### 1. Derive a color proposition from the product context

Read the available evidence and resolve only gaps that would change the direction:

- product purpose, subject/content, primary task, and use context;
- audience and actual users, cultural or regional context, platform, and environment;
- brand personality, voice, and the distinction that matters against relevant alternatives;
- existing logo, imagery, material, product color, competitors, and identity signals that must remain; and
- functional constraints from data, statuses, accessibility, relevant themes, and real backgrounds.

Turn that evidence into one mechanism sentence, such as: “Because `<purpose/users/context>`, color should use `<relationship or behavior>` to express `<brand personality/difference>` while keeping `<critical content/action>` clear.” The sentence must explain the later roles; “premium,” “warm,” and “modern” do not. Choose only the decision dimensions needed for this color judgement and apply the sector-default test below. The two-to-four axes in the full identity workflow are a comparison method for formal identity sets, not a required step for ordinary color work. Do not preselect temperature, lightness, chroma, candidate count, or color count.

Use external references only when a real question remains—for example, separating brand and semantic colors in this category or checking a cultural conflict. Project evidence can be sufficient; color selection does not require a catalog visit, moodboard, or imitation of another brand.

### 2. Define roles before exploring colors

Before selecting values, list the roles the product actually needs: canvas and surfaces, primary and secondary text, main brand expression, primary action, supporting action, borders and focus, selection, success/warning/error/information, data series, and overlays on imagery. Keep brand roles separate from semantic status roles. Do not create unused roles merely to make the system look complete. Design multiple themes only when the product supports them, while preserving role relationships and recognizable identity.

Explore relationships from the mechanism sentence. Hue, lightness, chroma, temperature, ground, adjacency or contrast, and visual weight in the real composition may all vary. The brief and content determine candidate count, color families, proportions, and style. Monochrome, analogous, multicolor, high-chroma, low-chroma, light-ground, dark-ground, or no decorative accent can all be valid. Do not default to green, dark, light, desaturated, saturated, a neutral base, a small accent, fixed proportions, fixed color counts, or a preset pair. Do not substitute generic color-psychology claims for a product-specific reason.

### 3. Settle the direction before UI color implementation

Compare candidates with the same representative content and target surface rather than isolated swatches:

1. Explain how each role answers the purpose, users, context, personality, and differentiation. Apply the sector-default test below and remove familiar answers that the brief cannot justify.
2. Inspect hierarchy, content density, image backgrounds, states, and interactions in a representative page or component; a logo or one button cannot stand in for the product.
3. Measure the actual text, control, focus, and required graphical contrast. Preserve non-color cues for state, and inspect relevant themes and the actual renderer or device.
4. Separate measured gates from judgement. Contrast and license results can reject a candidate; brand fit, differentiation, and expression remain reasoned design judgements, not conversion or universal psychology claims.

Settle the color direction, role relationships, and representative application before implementing color across the interface. If an unresolved brand choice would materially change the result, the user or authorized design owner chooses it. If design judgement has already been delegated, make a clear recommendation, record the rationale, and continue without adding an approval ceremony. Produce a full identity, logo/type system, or multiple formal identity sets only when the task requires them.

### 4. Hand off an implementable system

Deliver named roles and design tokens rather than loose hex values. For each role, record purpose, allowed foreground/background combinations, relevant theme mapping, semantic boundaries, and measured results. Record what was preserved, why the direction fits, how it differs from a generic sector answer, and which backgrounds or devices remain unverified. The real page still needs acceptance with representative content, states, responsive sizes, and interaction; a palette sheet or passing contrast script is not brand-experience acceptance.

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
