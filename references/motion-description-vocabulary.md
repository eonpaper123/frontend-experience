# Motion Description Vocabulary

Use this reference to translate conversational descriptions into precise, testable motion briefs before choosing code or media. The five scene phrases below are descriptive labels captured from a motion-design demonstration. They are useful prompt language, but they are not formal standards, library features, or proof of how an effect was implemented.

For established mechanics such as stagger, morph, parallax, transform origin, or spring, use an installed `animation-vocabulary` skill when available. The definitions in this file remain sufficient to write the behavior contract when it is absent. For implementation choices, continue to [Technology Selection](technology-selection.md).

## Compose a motion description

Build a label from:

`[trigger or input] + [motion shape] + [interaction or spatial outcome]`

- **Trigger or input:** hover/focus, click/tap, drag, scroll, cursor/pointer, device motion, or autonomous time.
- **Motion shape:** bloom, vortex, float, helix, luminous flow, orbit, growth, reveal, or another observed geometry.
- **Outcome:** opening, transit, navigation, inspection, emergence, state change, or ambient presence.

Then add the behavior contract the label cannot carry: controlled subject and properties, source and destination states, scroll or pointer bounds, holds, reverse/cancel behavior, touch/keyboard route, and reduced-motion result. Do not infer an autonomous loop from the word “float”, a scroll driver from a spiral visual, or a rendering stack from any label.

## Select and build pointer-responsive Hairline figures

Use this recipe for searches such as `Linear`, `HAIRLINE`, `hairline-create`, `figures`, `lineicons`, line art, isometric, pointer response, hover reveal, interactive illustration, standalone HTML, or microinteraction. Misreported names such as `figures`, Lucas Maystre, or `@lucasmaystre/lineicons` are not official project coordinates. The verified source is Lucas Marques's [Hairline](https://hairline.lucasmarkes.com/), [repository](https://github.com/lucasmarkes/hairline), and MIT-licensed package `@lucasmarkes/hairline`; the public [`hairline-create` skill](https://hairline.lucasmarkes.com/skill) creates a self-contained HTML figure. These are available sources, not globally installed capabilities or permission to add a project dependency.

Choose the smallest route that fits:

- Reuse the project's own illustration or component when it already expresses the needed metaphor and interaction language.
- Choose one verified Hairline figure when its subject and behavior fit; import only that figure, preserve its accessible label and theme contract, and record the MIT notice with third-party material. Do not install misreported alias names.
- Author a custom SVG/HTML figure, or use the official skill only when it is actually installed or installation is requested, when the product needs a distinct metaphor. Define the object, what the pointer changes, what the read-out says, the resting composition, and one bounded `intensity` parameter before drawing.

For either implementation, keep the interaction legible and stable:

1. Hit-test against fixed rest or target geometry, never the currently animated edge; animated layers must not move their own hit area out from under the pointer.
2. Spread response by distance from the active part and clamp its reach. Treat Hairline's published timing, falloff, spring, and frame values as source-specific defaults to test, not platform constants.
3. Give discrete choice and continuous pointer tracking different clocks: a bounded ease can settle “which item”, while a spring can follow “where the pointer is”. Update the target in input handling and let one animation loop own drawing.
4. Preserve isometric construction: rounded silhouettes, quieter interior creases, deliberate back-to-front occlusion, one meaningful stroke accent, and no text inside the drawing when geometry can carry identity.
5. Design the resting state and the leave/cancel return, not only hover. An `intensity` control changes response strength without changing the metaphor or allowing parts to overlap, escape the frame, or expose false occlusion.
6. If the figure is purely decorative or repeats adjacent text, hide it from assistive technology and keep its descendants unfocusable. Give an independent, meaningful but non-interactive illustration a concise image description without inventing keyboard focus. If it conveys selection or supports an action, provide equivalent focus, keyboard, touch, and announced-state behavior; pointer-only movement is not the product control.
7. Verify rest, near/far pointer positions, held-still hit stability, rapid crossing, leave/return, maximum intensity, theme contrast, target width, offscreen idle cost, and the deliberate reduced-motion state in the real surface.

## Five observed scene labels

| Scene label | Operational reading and required clarification |
| --- | --- |
| HOVER-TRIGGERED DOOR BLOOM INTERACTION | A defined hover or focus target makes door-like panels open radially. Specify the target, opening anchor, exit/reverse path, keyboard focus behavior, and touch action. |
| SCROLL-DRIVEN VORTEX TRANSIT | Scroll advances the viewpoint or subject through a vortex-like depth field. Specify the local scroll range, camera/subject ownership, endpoints, and whether the scene is programmable or pre-rendered. |
| IMMERSIVE FLOAT | A spatial composition creates a floating, enveloping impression. The source demonstration also contains a click, a falling sphere, and surface growth, so this label alone does not establish an ambient loop or the full event sequence. Name the actual trigger and stages. |
| SCROLL-DRIVEN HELIX FLOW | A helix-like light or object reveals multiple angles as progress changes. The narration describes downward dragging while the answer label says scroll-driven; confirm whether the product uses wheel/touch scroll, direct drag, or another progress source before implementation. |
| CURSOR-DRIVEN LUMINOUS FLOW | Pointer position drives a luminous field or flow. The demonstration also suggests camera advance, fog, and ground emergence; separate pointer-controlled properties from autonomous or scroll-controlled layers and give each property one owner. |

## Five observed UI motion patterns

The following labels and LIVE READOUT values come from a visual demonstration, not source code. They are prompt vocabulary and tuning references, not formal standards, implementation proof, universal constants, or implied product requirements. Write a brief as:

`[effect goal] + [technical means] + [parameters] + [coupling or threshold rule]`

Then name the actual input, controlled properties, source/destination and reverse/cancel states, touch and keyboard path, and reduced-motion state. Treat every numeric reading below as a sampled demonstration state unless the target product measures and adopts it deliberately.

### LIQUID GLASS

- **Brief:** Make the top bar read as a thick translucent layer; blur or distort the content beneath it, move its edge highlight with local scroll, and couple bar treatment and foreground ink to the underlying content luminance.
- **Observed samples:** `BAR.LUM 20% -> 93%`, `TEXT WHITE -> INK`, and `REFRACT x1.06 / 10px`.
- **Boundary:** `backdrop-filter: blur()` only softens the backdrop; it is not physical refraction. Call for refraction only when the implementation has a defined distortion/displacement layer. Verify foreground contrast against the actual changing content rather than copying the demonstrated WHITE/INK values. Map the scroll-owned properties through [Scroll-driven Motion](../SKILL.md#build-scroll-driven-motion-as-a-narrative-system), including reverse scroll and the reduced-motion still.

### AMBIENT GLOW

- **Brief:** Extract or receive a cover palette, render a large-radius soft glow around the cover, and interpolate the glow palette continuously when the cover changes.
- **Observed samples:** `GLOW R about 291–310px` and `BLEND about 99–100%`.
- **Boundary:** Those are demonstration readings, not a fixed radius or blend recipe. Browser pixel extraction is allowed only when the image is same-origin or grants the required CORS access; otherwise the brief must use an explicitly supplied palette rather than claim automatic extraction. Keep cover text and controls legible during the palette transition; reduced motion may switch directly to the next verified palette.

### DEPTH SCROLL

- **Brief:** Split the scene into foreground, middle, and far planes; drive their relative scroll movement, blur, and optional brightness from one local scroll progress source so reversing scroll reverses the depth relationship.
- **Observed samples:** `SPEED F/M/B 1 / 0.6 / 0.25`; `BLUR F/M/B 0 / 5 / 14`.
- **Boundary:** These three-layer values are a reference composition, not universal parallax ratios. Map this to [Scroll-driven Motion](../SKILL.md#build-scroll-driven-motion-as-a-narrative-system); keep essential readable or interactive content out of a blur-only layer, support touch/wheel and keyboard scrolling, and define a readable reduced-motion stage rather than merely disabling depth.

### CYLINDER SCROLL

- **Brief:** Use each row's signed distance from the viewport center to drive its cylinder-facing rotation, scale, and brightness/opacity; specify the center row, entry/exit behavior, and how the focused or selected row settles.
- **Observed samples:** top-row `ANGLE -62.1deg -> -48.1deg` and `SCALE 0.730 -> 0.791`.
- **Boundary:** The observed pair describes sampled positions, not a curve or a release threshold. This is scroll-position behavior under [Scroll-driven Motion](../SKILL.md#build-scroll-driven-motion-as-a-narrative-system); use the existing INERTIA picker rules only if the product also has release inertia and snap. Preserve logical reading/focus order, expose a keyboard selection route, and give reduced motion a flat but still centered/selected-list state.

### METABALL DRAG

- **Brief:** During drag, connect the dragged element to its origin with a liquid/metaball band that narrows with distance; define one intentional break threshold, then settle linked and snapped states visibly on release/cancel.
- **Observed samples:** linked at `DISTANCE 183px / NECK 7px` (also `154px / 11px`), linked at `0px / 68px`, and snapped/broken at `319px`. These are separate snapshots, not a sampled threshold curve.
- **Boundary:** Do not write `NECK 7 -> 68` as a causal distance formula, infer a break threshold of `319px`, or substitute the shown values for an implementation's measured rule. This visual label is not synonymous with **STICKY**: use the [STICKY drag contract](../SKILL.md#advanced-interaction-techniques) for follow, threshold, snap, cancellation, and keyboard/non-gesture review, but its `66px` reference is independent of this demonstration. Touch and pointer input must share the same drag model; reduced motion should communicate the linked or snapped result without relying on the stretching band alone.

Across all five patterns, the label does not establish the rendering stack or source implementation. Verify actual content contrast, touch behavior, keyboard/non-gesture parity, reverse/cancel behavior, and reduced-motion output on the target surface.

## Route the named effect

- Use [Scroll-driven Motion](../SKILL.md#build-scroll-driven-motion-as-a-narrative-system) when scroll controls programmable DOM, SVG, canvas, Three.js, camera, material, or shader state.
- Use [Scroll-driven Video](../SKILL.md#build-scroll-driven-video) when scroll seeks a pre-rendered linear journey whose camera, material, lighting, or semantic deformation is baked into video.
- Use the stateful-motion and interaction sections in [Frontend Experience](../SKILL.md) for hover, click, pointer, reveal, or reversible object-state behavior.
- When a brief names FAN, INERTIA, SHEET, PARABOLA, COLLAPSE, REORDER, FLIP, STROKE, STICKY, or page transition, use the [Advanced Interaction Techniques table](../SKILL.md#advanced-interaction-techniques) for its behavior contract and reference parameters; do not turn a descriptive scene label into a technique name.
- When the named effect is only the hook inside a one-loop participatory site, also read [Design playable, shareable micro-sites](../SKILL.md#playable-shareable-micro-sites) before choosing the layer.
- Select the rendering and animation layer only after the behavior contract is clear. A compound label may describe the same experience whether it is built with CSS/WAAPI, an existing animation library, WebGL/Three.js, shaders, or pre-rendered media.

When answering a naming request, lead with the closest label, mark it as a descriptive source label, and follow it with the underlying mechanics. When writing an implementation brief, use a sentence such as: “Scroll controls local progress; the camera moves through a vortex field from overview to interior; reversing scroll reverses the transit; reduced motion presents the named stage stills.”
