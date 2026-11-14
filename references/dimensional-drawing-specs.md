# Dimensional drawings for UI specifications

Use this reference for an anatomy sheet, redline, measured component specification, or a short structural-explainer film. It describes an existing interface; it does not replace implementation, design tokens, or runtime verification.

This guide is an independent synthesis informed by the MIT-licensed [Dimensional Drawing repository](https://github.com/enesozturk/dimensional-drawing), which contains both drawing and motion skills. Its license and repository structure were checked on 2026-11-15. No upstream examples, templates, or rendered assets are redistributed here.

## Six house rules

1. **Use monochrome drawing language.** Black lines, white paper, and controlled grays distinguish objects through line weight, dash pattern, hatching, and fill.
2. **Draw architecture rather than content.** Represent `TITLE SLOT / FLEX`, `CONTENT SLOT / FILL`, and `ACTION / HUG`; omit production copy unless the task specifically requires it.
3. **Label variables, not unexplained numbers.** Put codes on the drawing and define code, variable, value, and derivation in tables. A derived value should close, for example `R2 = R1 - B - S6 = 11`.
4. **Keep the sheet neutral.** Use an identifier such as `UI-CARD-001` rather than product names, logos, or marketing language unless the user explicitly requests branded documentation.
5. **Do not invent dimensions.** Mark unavailable values `[TBD]` and draw proportional schematics without presenting them as measurements.
6. **Measure the real subject.** Read the implementation or design source and inspect rendered boxes and computed styles. Survey all relevant component instances so the specification represents the system rather than one illustrative mockup.

`HUG` means content-sized, `FLEX` consumes remaining space, and `FILL` takes the parent width. These terms describe layout behavior; they are not substitutes for the target framework's actual constraints.

## Compact code system

| Prefix | Meaning | Examples |
| --- | --- | --- |
| `S#` | Spacing | container padding, stack gap, inset |
| `H#`, `Z#`, `I#` | Height, square size, icon size | header minimum, control size, icon |
| `B`, `W` | Border, width | border thickness, fixed or ranged width |
| `R#` | Radius | container, inset, control, pill |
| `Y`, `BL`, `SP`, `E#` | Shadow offset, blur, spread, envelope | top, side, and bottom extents |
| `T1`, `V1`, `MH` | Touch minimum, viewport margin, maximum height | `MH = 100vh - 2 * V1` |

Keep names project-specific and map them back to real design tokens. Codes on the drawing must have one corresponding row in a variable table.

## One-sheet structure

Prefer one readable sheet. Add another only when the first cannot contain the information legibly, and cross-reference the sheets explicitly.

### Title block

Place the title block outside the drawing SVG so its text does not scale. Include drawing number, revision, sheets, units, scale, source, scope, and two aligned note columns covering slots, codes, formulas, `HUG/FLEX/FILL`, `[TBD]`, and grayscale conventions. Show a small row of the most important variables and formulas.

### Main drawing

A source-informed reference canvas is an SVG `viewBox` of `0 0 1700 1060`, displayed inside a horizontally scrollable frame when the viewport is narrower. This is an adaptation example, not a universal physical sheet size.

Arrange:

- notes with numbered callouts at the upper left;
- a plan view with slot wireframes, dimension chains, centers, radius callouts, and detail circles;
- a shadow or keep-out envelope below the notes;
- an exploded axonometric stack showing canvas, scrim where applicable, shadow, container, inset surfaces, slots, and controls;
- nested-radius, control, and component-specific details along the bottom;
- spacing, size, radius, shadow, and viewport tables in the right column.

Use fine dimension and extension lines, heavier object outlines, dashed slots, dash-dot envelopes or centers, and hatching for cut or keep-out areas. Give tight labels explicit offsets instead of allowing overlap.

A source-specific drawing kit uses approximately `1.6 px` object outlines, `0.7 px` dimension lines, `0.55 px` extension lines with a `3 px` feature gap and `5 px` overshoot, `7 px` filled arrows, and `11 px` dimension text with a white knockout stroke. It uses `9 px` letter-spaced slot labels and `12 px` view titles with a `9.5 px` subtitle. These are coherent starting values for the 1700 by 1060 example canvas, not tokens to impose on another sheet size.

## Measure the existing interface

1. Identify the canonical component source, representative variants, and all usage sites.
2. Render it with the project's normal fonts and styles at the target states and breakpoints.
3. Read `getBoundingClientRect()` and relevant computed styles: padding, gap, radius, border, minimum height, flex behavior, minimum width, and overflow.
4. Distinguish authored tokens from incidental values produced by content or layout.
5. Count and inspect component instances so a one-off override does not become the published system.
6. Record missing or conflicting values as `[TBD]` or `CONFLICT`; do not average them silently.

For responsive components, specify behavior by breakpoint or container state. For overlays, include viewport placement, safe areas, keyboard effects, maximum height, scrim, and focus or dismissal ownership. For buttons and fields, separate visual bounds from touch target bounds.

Stageshow and other illustrative sources can establish composition for a demonstration; they are not evidence of real product measurements. Use actual implementation, design-source, or observed runtime values for a measured specification.

## Motion appendix

A structural-explainer film can reuse one SVG and one camera. Make `render(t)` a pure function of time so any frame can be rendered independently.

A source-informed five-beat example is:

1. close-up line drawing of the primary structure at roughly `4.4x` scale;
2. pull back toward roughly `1.7x` as the remaining plan resolves;
3. lift layers into an axonometric stack, drawing strokes before fills and offsetting the fill by about `0.55-1.25 s` in the source example to prevent a white flash;
4. reveal the full sheet near `1x`, with notes, tables, and details grouped in short `0.3-0.5 s` sequences;
5. finish with a very slow camera move, such as the source example's scale change from `0.998` to `0.988`.

Use logarithmic interpolation for large camera-scale changes. Let one event lead at a time: geometry before dimensions, leaders before labels, strokes before fills. Use ease-in-out for camera and line travel and ease-out for reveals. Avoid bounce, overshoot, color, and decorative motion that obscures the specification.

The upstream reference film uses an approximately 11-second, 1920 x 1080, 60 fps example with source-specific timing. Treat those values as an adaptation starting point, not a mandatory delivery format. Verify encoding and frame output in the chosen renderer.

## Observable acceptance

- Every drawing code exists in a table and every published formula closes.
- Values come from a named source or are marked `[TBD]`; conflicts are visible.
- Slot labels describe layout behavior without depending on production copy width.
- No accidental product branding or non-gray accent remains.
- The plan, details, exploded view, tables, and callouts remain legible at delivery size.
- A wide render has been inspected for overlaps, clipped labels, and objects crossing the sheet border.
- Motion frames can be rendered out of order with the same result because state derives only from time.
- The delivery states which source, revision, viewport, fonts, and component states were measured.
- A finished drawing or film is described as documentation, not proof that the component works in the product.

## Copyable task prompt

```text
Create a monochrome dimensional drawing for [component] from [repo/story/URL].
Measure the real implementation and representative variants. Use slots rather
than production copy, variable codes rather than unexplained dimensions, and
[TBD] for anything the source does not establish. Produce one title block and
one dense sheet containing notes, plan view, dimension chains, shadow or
keep-out envelope, exploded layer stack, important details, and variable
tables. Keep formulas closed and map values to project tokens. Render the
sheet at 1800 px wide and inspect overlap, clipping, and legibility.

If a structural-explainer film is required, animate the same SVG with a pure
render(t), a five-beat line-to-exploded-view sequence, and a camera that can
jump to any frame. Report the source revision, all [TBD] values, and what was
visually inspected. Do not present the drawing as runtime acceptance.
```
