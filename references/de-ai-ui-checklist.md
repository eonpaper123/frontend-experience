# De-AI UI: Business Clarity Before Decoration

Use this critique lens for requests to remove an "AI look," correct generic generated-looking UI, or polish a business dashboard, including a small component change. It is neither a universal style preset nor a way to determine whether AI authored a screen. Preserve the project's brand, contrast, accessibility, useful information density, and established style. For decision hierarchy and data semantics, also use [dashboard composition](dashboard-composition.md); do not restart a redesign for a local fix.

## Seven lessons

1. **Reduce competing surface effects.** When broad purple-blue gradients, glow, or glass obscure financial or operational content, identify which treatment competes with meaning and rebalance color, surface effects, and hierarchy from the actual brand, content, and task. Keep strong color where it carries brand, series, state, or action meaning. A black-and-gray treatment is one possible response, not a neutral-base default or a ban on branded color, gradients, glass, or light themes.
2. **Remove decorative hype from metrics.** Replace emoji and exaggerated punctuation such as `+12%!!` with a readable value and a valid comparison such as `+12% vs last month`. Keep meaningful icons and accessible labels; punctuation alone does not prove poor design.
3. **Write operational copy.** Prefer the actual reporting period, metric name, unit, and comparison basis over promotional greetings or excitement. Distinguish percentage change from percentage-point change, and month-over-month from year-over-year. A named month is an example, not a reporting period to hard-code.
4. **Simplify component framing.** When pills, badges, and oversized radii all compete, reuse the project's ordinary card geometry, restrained borders, and fewer status decorations. Preserve genuine tags, filters, severity markers, and adequate interaction targets. Quiet separators must not erase boundaries needed to identify controls or understand data.
5. **Make hierarchy follow real tasks and data.** Distinguish navigation, page identity, metric summaries, and chart or detail regions by purpose. Use actual amounts, periods, and plan or member counts when relevant. Never invent production metrics or add irrelevant KPIs to make a mockup feel real. Clearly label illustrative data and show honest empty and error states when data is unavailable.
6. **Use a stable spacing system.** Reuse project spacing tokens for grouping, alignment, and density instead of random large gaps. `8/12/16/24` is an example, not a required scale. Account for content, localization, zoom, and target sizes instead of enforcing one pixel ladder.
7. **Make charts interpretable.** Choose appropriate axes, scales, units, time ranges, series labels or legends, and positive/negative treatment when the data requires them. Do not add meaningless negative zones or redundant legends to every chart. Replace decorative bars or glow with truthful scale and comparison; preserve readable labels and non-color cues.

## Changed-surface self-check

Apply these questions only to the changed surface. The suggested corrections are candidates when a treatment harms the task, not automatic replacements.

1. Do large purple-blue gradients, glow, or glass compete with content? Reassign color and effect weight from the actual brand, content, and task; keep intentional brand and semantic treatment that remains readable instead of automatically replacing it with a neutral base.
2. Do emoji, repeated punctuation, or promotional welcome copy compete with business meaning? Use neutral operational copy and the actual period or comparison basis.
3. Do pills, colored badges, and oversized corners all demand attention? Consolidate them into project radii, restrained borders, and a few meaningful status markers while keeping control and status semantics.
4. Is the displayed data specific and credible? Check amounts, currency, periods, comparison basis, and plan or member counts against the source. Never manufacture production values.
5. Does spacing follow a stable project scale? Treat `8/12/16/24` only as an illustration of consistency.
6. Do charts behave like a real product? Verify scale, units, time range, direct labels or legend, and sign treatment as applicable, using representative data and accessible output.

Inspect the resulting target surface, not only its source: hierarchy, label wrapping, focus, contrast, responsive density, and representative data must remain usable. Use the core skill's verification gate; this checklist does not replace runtime acceptance.

<a id="squint-test"></a>
## Blur-assisted spacing check

Use this check when spacing, whitespace, or visual balance feels wrong even though the boxes are numerically aligned. Start from the established grid and spacing tokens, then temporarily suppress detail so visual weight is easier to compare. This is also useful outside de-AI critiques.

**Set up the comparison.** Capture the current UI at its intended display size, duplicate the screenshot, and blur the duplicate until glyph detail recedes but groups remain distinguishable. A radius around `1–3%` of the reviewed region's short side is only a starting experiment; adjust for region size and display zoom. A temporary DevTools `filter: blur(12px)` on the inspected region is another preview, not production styling or a universal radius. Use the screenshot route when a live filter changes layout or positioning. Compare against the unblurred original, hide selection guides, and change one factor at a time.

1. **Surrounding whitespace weight:** inspect all four sides and adjacent groups for an unintended heavy or cramped edge. Preserve deliberate asymmetry and hierarchy; equal perceived weight does not require equal pixel values.
2. **Icon inside its control:** check whether the visible shape looks too high, low, left, or right. An icon may already be optically corrected. Keep any justified adjustment inside the component while preserving the external grid, hit area, and focus geometry.
3. **Text-block side margins:** compare visible glyph edges with the intended text and container alignment, not only the text box. Correct an unintended cramped side while respecting font metrics, baselines, reading direction, and composition. Do not center every text block or force left/right equality. Reuse [responsive typography](responsive-typography.md) for type-system checks.
4. **Card inner and outer spacing:** judge the relationship among content padding, intra-card groups, and gaps between cards. Express grouping with the project's token scale. Proportional rhythm is the goal, not identical inner/outer distances or a fixed ratio.

Remove the blur and compare before/after at actual size and at the relevant viewport, theme, text-size, and zoom states. Recheck optical balance, glyph and baseline alignment, wrapping and clipping, focus visibility, hit areas, and actual text/control contrast. Accept only a correction that still works in the real UI. Blur suppresses detail while grayscale removes color cues; either can reveal a problem, but neither replaces contrast measurement, accessibility checks, interaction testing, or runtime acceptance.

<a id="color-review"></a>
## Color review

When color itself is the reported problem, diagnose the changed surface before replacing its palette. If the optional `color-audit` skill is available, use it for this bounded review; otherwise apply the same core checks directly.

1. Identify the actual failure: a muddy gradient, a vibrating boundary between similarly strong colors, merged adjacent shapes, a missing focus boundary, or an accent that overwhelms the task.
2. Preserve existing brand and semantic tokens first. Candidate repairs include choosing adjacent hues, inserting an intentional intermediate stop, declaring the interpolation color space, adding a neutral separator, outlining one shape, or reducing the accent's area.
3. Inspect color and grayscale at the real component size, in supported themes, and across the states that matter. Measure actual text, control, focus, and graphical-object contrast rather than judging a palette swatch alone.
4. If the diagnosed boundary or silhouette fault calls for local geometry, a `1–4 px` divider or `1–2 px` outline is an adjustable component-level starting point, not a palette rule or acceptance quota. Derive color area and visual weight from the [brand-color method](brand-identity-system.md#brand-color-system), content, and actual composition rather than a fixed ratio.

Use the actual browser or platform renderer when gradients matter; interpolation behavior depends on the chosen color space and implementation. [CSS Color 4](https://www.w3.org/TR/css-color-4/#interpolation-space) defines the relevant web interpolation concepts. This section is an independent synthesis, includes no source media, and does not claim that a target surface was rendered or accepted.

## Source and limits

This independent checklist was derived from a supplied @heydamir EmberAI financial-dashboard before-and-after breakdown. The comparison images and reported pixel annotations are not included and were not independently inspected for this reference, and no usability improvement was measured. This document preserves the reusable critique while making no claim about authorship, production performance, or a rendered result.
