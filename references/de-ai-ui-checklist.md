# De-AI UI: Business Clarity Before Decoration

Use this critique lens for requests to remove an "AI look," correct generic generated-looking UI, or polish a business dashboard, including a small component change. It is neither a universal style preset nor a way to determine whether AI authored a screen. Preserve the project's brand, contrast, accessibility, useful information density, and established style. For decision hierarchy and data semantics, also use [dashboard composition](dashboard-composition.md); do not restart a redesign for a local fix.

## Seven lessons

1. **Reduce competing surface effects.** When broad purple-blue gradients, glow, or glass obscure financial or operational content, simplify to controlled neutral surfaces and reserve stronger color for meaningful series, states, and actions. A black-and-gray treatment is one possible response, not a ban on branded color, gradients, glass, or light themes.
2. **Remove decorative hype from metrics.** Replace emoji and exaggerated punctuation such as `+12%!!` with a readable value and a valid comparison such as `+12% vs last month`. Keep meaningful icons and accessible labels; punctuation alone does not prove poor design.
3. **Write operational copy.** Prefer the actual reporting period, metric name, unit, and comparison basis over promotional greetings or excitement. Distinguish percentage change from percentage-point change, and month-over-month from year-over-year. A named month is an example, not a reporting period to hard-code.
4. **Simplify component framing.** When pills, badges, and oversized radii all compete, reuse the project's ordinary card geometry, restrained borders, and fewer status decorations. Preserve genuine tags, filters, severity markers, and adequate interaction targets. Quiet separators must not erase boundaries needed to identify controls or understand data.
5. **Make hierarchy follow real tasks and data.** Distinguish navigation, page identity, metric summaries, and chart or detail regions by purpose. Use actual amounts, periods, and plan or member counts when relevant. Never invent production metrics or add irrelevant KPIs to make a mockup feel real. Clearly label illustrative data and show honest empty and error states when data is unavailable.
6. **Use a stable spacing system.** Reuse project spacing tokens for grouping, alignment, and density instead of random large gaps. `8/12/16/24` is an example, not a required scale. Account for content, localization, zoom, and target sizes instead of enforcing one pixel ladder.
7. **Make charts interpretable.** Choose appropriate axes, scales, units, time ranges, series labels or legends, and positive/negative treatment when the data requires them. Do not add meaningless negative zones or redundant legends to every chart. Replace decorative bars or glow with truthful scale and comparison; preserve readable labels and non-color cues.

## Changed-surface self-check

Apply these questions only to the changed surface. The suggested corrections are candidates when a treatment harms the task, not automatic replacements.

1. Do large purple-blue gradients, glow, or glass compete with content? Try neutral surfaces with restrained semantic color, while retaining intentional brand treatment that remains readable.
2. Do emoji, repeated punctuation, or promotional welcome copy compete with business meaning? Use neutral operational copy and the actual period or comparison basis.
3. Do pills, colored badges, and oversized corners all demand attention? Consolidate them into project radii, restrained borders, and a few meaningful status markers while keeping control and status semantics.
4. Is the displayed data specific and credible? Check amounts, currency, periods, comparison basis, and plan or member counts against the source. Never manufacture production values.
5. Does spacing follow a stable project scale? Treat `8/12/16/24` only as an illustration of consistency.
6. Do charts behave like a real product? Verify scale, units, time range, direct labels or legend, and sign treatment as applicable, using representative data and accessible output.

Inspect the resulting target surface, not only its source: hierarchy, label wrapping, focus, contrast, responsive density, and representative data must remain usable. Use the core skill's verification gate; this checklist does not replace runtime acceptance.

## Source and limits

This independent checklist was derived from a supplied @heydamir EmberAI financial-dashboard before-and-after breakdown. The comparison images and reported pixel annotations are not included and were not independently inspected for this reference, and no usability improvement was measured. This document preserves the reusable critique while making no claim about authorship, production performance, or a rendered result.
