# Icon Selection and State Transitions

Use this reference for a new UI, icon-source selection, or a meaningful icon-state transition. Search for reusable source first and preserve the project's icon language. A candidate library is neither installed nor automatically licensed for the target product, and an animated demo is not a reason to replace an existing icon system.

## Selection order

1. **Target-platform symbols.** For a native interface, inspect the platform's symbols and native state behavior first. Do not apply a system font merely because a web page runs in a Windows or macOS browser.
2. **Existing design system and brand.** Preserve established symbols, sizes, weight, stroke, and semantic mapping. Use approved logo assets for brand identity rather than assembling a trademark from generic icons. Platform-first is an inspection order, not a forced migration away from a coherent project system.
3. **One suitable general library.** Choose a library whose language and coverage fit the project, then verify its target framework, tree-shaking or selective import path, current license, and exact symbol coverage.
4. **Custom SVG.** Draw a new symbol only when the first three sources cannot express required meaning or brand identity. Record the missing semantic, and standardize viewBox, stroke or fill treatment, optical size, naming, and accessible name. Drawing an icon does not justify writing a morph-interpolation engine.

## Source matrix

| Surface or need | Candidate and boundary |
| --- | --- |
| Native iOS or macOS | [SF Symbols](https://developer.apple.com/sf-symbols/), following target-OS availability, weight, and scale. Review Apple's usage restrictions; the symbols are not a cross-platform open-source export set. |
| Windows or Fluent | [Fluent System Icons](https://github.com/microsoft/fluentui-system-icons) or [Segoe Fluent Icons](https://learn.microsoft.com/en-us/windows/apps/design/iconography/segoe-fluent-icons-font). The SVG library and system font have different licensing and deployment conditions. |
| Android or Material | [Material Symbols](https://developers.google.com/fonts/docs/material_symbols). Use the variable axes for fill, weight, grade, and optical size when they already express the required state. |
| General web or SaaS | [Lucide](https://lucide.dev/) is a useful default candidate when the project has no icon system. Its consistent stroke language is not a reason to replace an established library. |
| Tailwind project | [Heroicons](https://heroicons.com/), selecting outline or solid by the design language. Tailwind does not require Heroicons. |
| Dense enterprise tables and tools | [Tabler Icons](https://tabler.io/icons), after checking business-symbol coverage and recognition at the real compact size. |
| Multiple weights or styles | [Phosphor](https://phosphoricons.com/), with a fixed semantic purpose for each style rather than arbitrary mixing. |
| Brand or product identity | An approved custom SVG or original brand asset. Do not redraw a trademark in a generic library's style. |
| Menu to close, play to pause, sun to moon, outline to fill, or a justified cross-library transition | [Morphicons](https://morphicons.com/llms-full.txt) can own the glyph morph after checking whether the platform or existing component already provides the behavior. Cross-library pairs need viewBox, stroke or fill, and optical alignment; they do not justify mixing unrelated icon styles across the product. |

## Morphicons integration contract

Morphicons is optional. Before integration, inspect its current official documentation, confirm project and framework compatibility, and obtain authorization for any new runtime dependency. The official documentation checked on 2026-10-30 uses:

```sh
npm install morphicons
```

Use the project's package manager. The examples also require Lucide icon data when Lucide nodes are selected; that data is distinct from the `lucide-react` component package.

- For ordinary state changes, provide the current `icon`. Use controlled `from`, `to`, and `progress` only when a real gesture or scroll position owns progress. The imperative `morphTo()` and `set()` APIs are alternatives for necessary sequences; do not let multiple mechanisms control the same glyph geometry.
- The documented spring options include `snappy`, `smooth`, `bouncy`, or a stiffness and damping object. Treat those as library controls, not product timing defaults. Size, color, stroke width, and absolute stroke-width behavior should remain consistent with the selected icon source.
- Give the icon its own label only when it carries standalone meaning. When a surrounding button already has an accessible name, keep the inner decorative icon hidden to avoid duplicate announcements. Set `reducedMotion="user"` when the transition should follow the user's system preference; the documentation's current default is `never`, so omission is not equivalent.
- Input can be an icon node or path data. For external SVG, use the documented adapter or build-time preprocessing, preserve the real viewBox, and retain fill information. Do not assume every source uses a 24 by 24 coordinate system or convert a filled shape into an open stroke path.
- Current filled-region support treats both ends as filled when either endpoint is filled. Its region code loads when first needed and is documented at about 5.4 KB gzip; that is a version-specific cost. For long lists on constrained devices, inspect build-time region preprocessing. The documented mask and canvas targets remain stroke-only.
- The documentation describes server rendering of the final SVG. The product must still verify initial state, hydration, first filled-code load, repeat toggles, and interrupted transitions. Documentation is not proof that the target project cannot flash or mismatch.
- Morphicons owns glyph geometry only. Button containers, cards, layout, pending state, success state, and business authority remain in the product's existing state and motion system.

## Accessibility, performance, and rights

- Hide decorative icons. Name standalone meaningful icons. Put actions in native buttons, links, or equivalent platform controls; pair ambiguous symbols with visible text instead of relying only on a hover tooltip.
- A product may choose a 44 by 44 minimum hit area, expressed in CSS pixels on the web or the platform's native unit. That value is a hit target, not the icon canvas, and is not a universal WCAG AA requirement: [WCAG 2.5.5 Target Size (Enhanced)](https://www.w3.org/WAI/WCAG22/Understanding/target-size-enhanced.html) is AAA and includes exceptions. Measure applicable contrast on the actual symbol, text, focus, and background combinations.
- Import only selected icons. Reserve animation for meaningful state changes, and verify forward and reverse transitions, repeated activation, cancellation, keyboard, touch, reduced motion, server rendering, and the real cost of dense lists on target devices.
- Morphicons currently states an MIT license. Lucide, Tabler, Heroicons, Material Symbols, Phosphor, and platform fonts or symbol sets each retain their own terms. Check the selected version and preserve required notices before adoption; commercial use does not remove license conditions.

Avoid mixing several uncoordinated icon families, changing the symbol for the same meaning across screens, hand-writing path interpolation for an existing behavior, or presenting a morph as evidence that an operation succeeded. This reference includes no icon assets, library source, installed dependency, build, or rendered verification.
