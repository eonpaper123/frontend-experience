# Responsive typography

Use this reference when establishing or materially changing a responsive type system. The goal is a durable hierarchy that works with real content, real font metrics, language, localization, zoom, and platform text scaling—not a copied screenshot scale.

## Production rules

1. **Separate semantics from appearance.** Choose `h1`–`h6` from document structure, then map them to visual roles such as display, title, heading, label, and body. Do not change heading level merely to obtain a size, and do not assume every `h1` must use the largest display token.
2. **Build roles from content and containers.** Define only the roles the product needs. Use `rem`/`em`, unitless line-height, and `clamp()` only when fluid interpolation improves the real layout. Breakpoints belong to content failure points, not to a specimen's device labels.
3. **Measure text in the script being shipped.** A Latin measure expressed in `ch` is at most a starting hypothesis. For Chinese and mixed CJK/Latin content, inspect actual characters per line, punctuation, word breaking, scanning, and reading context; do not apply an English character-count target mechanically.
4. **Tune line-height with the actual font.** Size, weight, x-height, script, column width, and density all affect vertical rhythm. Headings often need a tighter line-height than body copy, while Chinese or mixed-script paragraphs can require more room. Validate rather than copying a percentage.
5. **Treat tracking as typeface-specific.** Start from the font's kerning/default tracking. Broad negative tracking—especially in body or CJK text—can create collisions and poor punctuation rhythm. Verify uppercase, numerals, variable-font optical sizing, fallback runs, and every weight actually used.
6. **Validate font delivery.** Confirm the intended family and glyph coverage, correct weight files or variable axes, fallback metric shifts during loading, and synthetic bold/italic behavior. A design review performed with a missing or substituted font is not type-system acceptance.
7. **Accessibility is a layout state.** Preserve browser zoom and platform text scaling. Verify at 200% browser zoom where applicable, narrow reflow, long localized labels, large text/Dynamic Type on native targets, and that content is neither clipped nor replaced by ellipses where meaning is lost.

## Observed marketing-page specimen

The table sizes are CSS-pixel examples transcribed from a responsive-typography demonstration; Desktop 1440 / Tablet 1439–800 / Phone labels are not mandatory breakpoints. Native platforms retain their own text styles and scaling. No source media or font assets are included.

The demonstration showed one responsive marketing-page treatment. Keep these numbers only as provenance and a test specimen—not global defaults:

| Token in source | Desktop | Tablet | Mobile |
| --- | ---: | ---: | ---: |
| H1 | 80 | 64 | 44 |
| H2 | 56 | 56 | 32 |
| H3 | 32 | 32 | 28 |
| H4 | 20 | 20 | 18 |
| Large body | 18 | 18 | 16 |

The same specimen proposed body line-height `140–175%`, heading line-height `100–120%`, Latin line length `50–60` characters, body tracking `-2%`, heading tracking `-6%`, and all-caps tracking `+1%`. These are source-example values, not universal defaults. They require re-evaluation for the chosen font, language, content density, and accessibility target; the negative tracking values are especially unsuitable as an automatic CJK rule.

## Acceptance pass

If deliberately translating design-tool tracking relative to font size, −2%/−6%/+1% correspond to −0.02em/−0.06em/+0.01em; do not adopt them automatically. `ch` measures the zero-glyph advance, not arbitrary characters or Chinese character count. Keep user text-spacing overrides usable without clipping, and avoid viewport-only font sizing that defeats enlargement.

- Render representative short and long headings, paragraphs, lists, data, names, URLs, and error/status text—not lorem ipsum alone.
- Include Chinese, Latin, mixed-script, punctuation-heavy, numeric, and localized samples that the product will actually show.
- Inspect all shipped font weights after the webfont or app font has loaded, plus the intended fallback/loading state.
- Check target viewport widths, orientation or window resizing, 200% zoom where applicable, and native text scaling.
- Confirm semantic outline separately from visual hierarchy with accessibility tooling or the rendered accessibility tree.

## Editorial text pass

Apply this pass after the structural type roles exist. It sharpens editorial reading without forcing one specimen's font, scale, or language rules onto the product.

1. **Make hierarchy express meaning.** Title, section, body, metadata, label, and caption roles should follow document priority and semantics. A hierarchy can fail when every level looks the same or when one display size overwhelms everything; the fix is not automatically a larger heading.
2. **Tune line height with the real font and language.** `1.5` is a useful body-text starting point, while display headings often need a tighter value. Test the chosen font, weight, language, container, zoom, and user overrides rather than treating either number as a fixed token.
3. **Control measure by script.** A `45–75` character range is a familiar Latin-reading candidate, not a universal count for CJK text. Judge Chinese, Japanese, and Korean measure by ideographic density, punctuation, line breaking, and the actual reading context.
4. **Limit arbitrary display-font changes, not legitimate font roles.** A two-font guideline is a restraint against unrelated decorative faces, not a technical cap. CJK and Latin coverage, code, numerals, fallbacks, brand requirements, and font licensing can require more than two files or families.
5. **Handle mixed CJK and Latin text without rewriting copy.** A source suggestion of roughly one quarter of an ideographic character's width can be a visual spacing candidate. Do not automatically insert spaces or alter user-authored content; check copying, search, selection, input, and localization before changing text or markup.
6. **Respect language-aware punctuation and line breaking.** Avoid an isolated final character when a clean reflow is possible, but do not scatter nonbreaking spaces or hard line breaks that create overflow. Set the correct language metadata and test the target engine's real behavior. [Requirements for Chinese Text Layout](https://www.w3.org/TR/clreq/) is a reference for Chinese composition, not a guarantee of browser support.

Inspect desktop and narrow layouts, zoom, user font scaling, fallback fonts, mixed-script copy, long unbreakable strings, selection, and print if print is in scope. This section defines a future review pass and makes no rendered-page claim.
