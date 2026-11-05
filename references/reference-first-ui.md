# Reference-first UI and glass refraction

Use this reference when a new interface has no settled visual direction, when the supplied references do not answer the current design question, or when a generic template choice is producing an undifferentiated result. It combines a bounded reference-first workflow with a technical appendix for refractive glass. It is not a component library, a required research ceremony, or a replacement for the project's design system, [reuse index](ui-resource-index.md), [de-AI critique](de-ai-ui-checklist.md), or runtime acceptance.

For a small change inside an established direction, continue with the existing system. For an unresolved direction, research only the decision that blocks implementation.

## Select references by the missing decision

Start with the user's references, product content, current components, and brand rules. Identify the unresolved question before opening an external catalog. Record the specific example URL or local artifact, what was actually observed, and the implementation decision it changes.

| Missing decision | Candidate source | Extract |
| --- | --- | --- |
| Screen structure or task flow | [Mobbin](https://mobbin.com/) | Entry point, information grouping, screen sequence, and important states |
| Interaction detail | [Design Spells](https://designspells.com/) | Trigger, controlled object, feedback, result, return, and interruption |
| Visual exploration | [Recent](https://recent.design/) | Composition, pacing, image treatment, and expressive candidates |
| Brand-system structure | [Brand Guidelines](https://brandguidelines.net/) | Color roles, type hierarchy, mark use, and how rules are organized |
| Pitch or presentation structure when the task actually includes it | [Deck.gallery](https://www.deck.gallery/) | Narrative order, information grouping, and page composition |

These are optional entry points, not a five-site checklist. A catalog preview does not prove that an example is official, current, reusable, downloadable, or licensed for product use. Trace brand guidance and assets to their real owner and terms. A video demonstrates appearance or behavior; it does not automatically provide source code or a reusable component. If access is limited, state what was not inspected instead of filling the gap from search snippets.

## Turn a reference into an implementation decision

Extract evidence that can change the build:

- grid, alignment, and container relationships;
- spacing rhythm and information density;
- heading, body, label, and numeric type roles;
- color roles and contrast relationships;
- content hierarchy and realistic content volume;
- relevant states, triggers, and interaction outcomes;
- which project components and tokens can carry the result.

Then state what will be adopted, what will be rejected, and where the adaptation lands in the current project. Words such as “premium,” “clean,” or “modern” do not define an implementation. Measurements estimated from screenshots are not the source product's tokens, and an interaction that was not exercised is not verified behavior.

Use two or three directions only when a real choice remains. Keep the same content, viewport, and required states across directions so the comparison is about design. Recommend one and explain why. After a direction is selected, implement a representative page or core interaction before spreading it through the product.

### Copyable prompt: reference-led implementation

```text
Before writing UI code for <task and target platform>, inspect the supplied
references, current product, existing components, and brand rules. Name the
specific design question that remains unresolved. Select only a few accessible
references that answer it.

For each reference, describe the concrete grid, spacing rhythm, type hierarchy,
color roles, content density, and relevant interaction states. State what should
be adopted, what does not fit this product, and how the useful parts map to the
existing components and tokens. Do not infer source tokens from screenshots or
claim behavior that was not exercised.

Preserve <brand, data contract, platform, and scope>. Implement the selected
direction first on <representative page or component>. Compare the rendered
result at <target sizes and input modes>, then report the observed differences
and any behavior that remains unverified.
```

### Copyable prompt: bounded local improvement

```text
Change only <agreed local surface>. Use <specific reference URL or local
artifact> to correct <actual hierarchy, grouping, spacing, or interaction
problem>. Explain why the reference fits and the exact adaptation being made.
Preserve the rest of the product, brand, and behavior. Deliver an observed
before/after comparison on the target surface and identify anything not tested.
```

## Eight anti-template checks

These checks protect decisions; they do not impose a universal skin.

1. **Color has a job.** Keep brand and semantic colors when they work. A purple-blue gradient is neither automatically wrong nor a default solution.
2. **The first view has hierarchy.** The primary task, important content, and next action are findable. A centered heading can still be correct.
3. **Layout follows content.** Equal cards fit equal-weight content; unequal importance needs visible weight. Neither asymmetry nor a three-card row is a quality gate.
4. **Surface rules are coherent.** Radius, border, shadow, and elevation use the project's semantic scales. Do not create an arbitrary global maximum count.
5. **Type roles are readable.** Build contrast from content role, language, viewport, and accessibility needs. Do not require a fixed number of type levels on every component.
6. **Content is truthful.** Use real data or clearly labeled illustrative content to test density. Do not invent metrics or tables to make a design look complete.
7. **Required states exist.** Cover the focus, pressed, selected, disabled, loading, success, failure, and touch behavior the actual control needs. Do not add states merely to reach a quota.
8. **Every reference changes a decision.** Link it to a concrete adoption or adaptation and verify the result on the target surface. A source list or passing document check is not visual acceptance.

Common failure modes include collecting links without extracting decisions, copying another brand, adding asymmetry or motion solely to look less generic, applying glass across content, and extending a direction across the product before one representative surface has been reviewed.

<a id="glass-ruler"></a>
## Glass Ruler: refraction, dispersion, and edge reflection

Use this appendix only when the experience calls for a lens or refractive glass material. First use the [glass-mechanism selection guide](technology-selection.md#select-glass-materials-by-mechanism) to distinguish native material, backdrop blur, displacement, and real sampled refraction. The method below is a screen-space approximation driven by surface geometry; it is not full ray tracing or a physically calibrated glass material.

| Mechanism | Implementation contract | What to inspect |
| --- | --- | --- |
| Refraction | Define a surface normal and height, calculate a refracted direction from the incident direction and index ratio `eta = nIncident / nTransmit`, intersect it with the sampling plane, then map that position into the sampleable layer or texture. `1 / ior` is only the special case where the incident medium is approximated as air. Keep geometry, sampling, and scale in the same coordinate system. | Use grids, ticks, or text to reveal local bending and magnification. Content outside the lens should retain its intended geometry. |
| Dispersion | Sample red, green, and blue with slightly different dimensionless indices and composite them with correct alpha. The source's `0.01–0.03` difference is an unvalidated tuning example, not a material constant or verified offset budget. | Compare dispersion off and on. Edge color must not destroy label or tick readability. |
| Fresnel or edge reflection | Derive reflection weight from the angle between normalized surface normal and view direction, then combine it with a defined environment or deliberate stylized highlight. | Change shape and view direction. A fixed white outline is not evidence that the relationship is correct. |

### SwiftUI and Metal sampling contract

- [SwiftUI `layerEffect`](https://developer.apple.com/documentation/swiftui/view/layereffect(_:maxsampleoffset:isenabled:)) applies its shader to a raster layer created from the modified view. The shader position is the user-space coordinate of the destination pixel, and the layer sample comes from a subregion of that rasterized content. It does not provide arbitrary access to the page or screen behind the view.
- If the shader samples away from the destination position, `maxSampleOffset` must state the maximum sampling distance on each axis for all source pixels. Derive it from the actual displacement in the same coordinate space, and verify current API availability against the project's SDK and deployment targets. Preserve the layer's premultiplied RGBA when recombining separately sampled channels; an offset example from another surface is not a universal radius, texture size, or minimum.
- [`drawingGroup`](https://developer.apple.com/documentation/swiftui/view/drawinggroup(opaque:colormode:)) creates an offscreen-rendered group; it is not proof of better performance or a guarantee that every embedded platform view can be sampled. Use `opaque: true` only when the rendered content is actually opaque.
- Treat [Reduce Transparency](https://developer.apple.com/documentation/swiftui/environmentvalues/accessibilityreducetransparency) and reduced motion as different preferences. Reduced transparency needs an opaque, information-complete presentation; reduced motion needs a stable motion state.

Sample code values such as `660 * scale`, `364 * scale`, or `300 * scale` describe a particular experiment. They are not recommended defaults. Too small a sampling bound can clip or corrupt edges, while an arbitrarily large value does not repair a wrong coordinate model.

### Web translation

SVG `feDisplacementMap` can provide controlled displacement from an explicit input. A WebGL shader can sample a supplied texture or render target for refraction and per-channel dispersion. Decide how the background becomes a sampleable input; do not assume SVG, canvas, or a shader can read arbitrary DOM content behind it. CSS backdrop blur does not implement the refraction contract above.

[Maxime Heckel's refraction and dispersion tutorial](https://blog.maximeheckel.com/posts/refraction-dispersion-and-other-shader-light-effects/) is a useful implementation reference. Verify the chosen example's current library version, code and asset license, and project performance before reuse; this repository includes none of its code or media.

Prototype one bounded lens before expanding the material. Exercise pointer and touch movement, sampling near every edge, different backgrounds and themes, resize and zoom, actual frame time, Reduce Transparency, reduced motion, and the readability of content and focus. Glass area, resolution, and sample count all affect cost. A shader label or successful build does not establish performance or usability.

## Rights and evidence boundary

This reference is an independently written method. It redistributes no catalog preview, brand asset, source screenshot, video, or tutorial code. External sources remain subject to their own access and license terms. The prompts and checks are instructions for future project work, not evidence that any external catalog was accessed or that a refractive effect was implemented and accepted.
