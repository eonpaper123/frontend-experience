# GSAP, Lenis, and React Bits selection

Use this reference for multi-part web animation choreography, deliberate smooth scrolling, or one specific React effect component. It is not a mandatory three-library stack. Reuse the project's existing capabilities; keep CSS or WAAPI when they are sufficient. DOM libraries do not transfer directly to native apps or Mini Programs.

## Verified snapshot: 2026-11-08

| Candidate | Verified snapshot | License and selection boundary |
| --- | --- | --- |
| GSAP | npm latest is `3.15.1`. Framework-independent JavaScript; React may optionally use `@gsap/react` for lifecycle integration. | The [GSAP Standard License](https://gsap.com/standard-license/) is not MIT. Verify the current terms for the product, retain required notices, and ask the rights holder when the product may compete with restricted visual animation-building uses. Do not describe it as unrestricted open-source redistribution. |
| Lenis | npm latest and GitHub latest release are `1.3.27`; core is JavaScript with React and Vue integration routes. | [Lenis v1.3.27 is MIT](https://github.com/darkroomengineering/lenis/blob/v1.3.27/LICENSE); retain the notice. Choose it only when the experience requires controlled smooth scrolling or a shared scroll time source. Do not rewrite ordinary form, reading, or workspace scrolling by default. |
| React Bits | Reviewed at commit [`4dc7b5b`](https://github.com/DavidHDev/react-bits/commit/4dc7b5b7772e1217c8fb8d2a7aa074302180e5b4). It provides copyable React/Next.js variants rather than one package version suitable for every component. | The reviewed [license](https://github.com/DavidHDev/react-bits/blob/4dc7b5b7772e1217c8fb8d2a7aa074302180e5b4/LICENSE.md) is MIT plus a Commons Clause condition: components may be used as part of an application, website, or product, but the components, tools, sounds, or exports cannot be sold, sublicensed, or redistributed as standalone components, bundles, ports, hosted copies, or asset/template packs. Do not copy its reusable blocks into this MIT skill repository. |

Versions are a dated selection snapshot, not an instruction to upgrade a project. Review the actual source file, dependencies, client/SSR boundary, and current terms for the chosen component. Registry or copy commands can edit project dependencies and configuration; inspect their changes and select only the needed files.

## Ownership and lifecycle rules

1. **Choose choreography and scrolling separately.** GSAP owns timelines and animated properties; ScrollTrigger relates animation to scroll. Lenis owns smooth scrolling only when selected. ScrollTrigger does not require Lenis. Do not run Lenis, ScrollSmoother, another smooth-scroll engine, and conflicting native CSS smooth-scrolling behavior at the same time. One property cannot be written concurrently by GSAP, CSS, and another motion runtime.
2. **Register only used plugins and clean up locally.** Initialize DOM animation after client mount. Use the project's lifecycle tools or scoped `gsap.context()` and `matchMedia()` cleanup for the component's animations, triggers, and styles. Do not globally kill other pages' work. React Strict Mode remounts, route exit, and resize must not leave duplicate listeners or timelines.
3. **Run one Lenis clock.** Use either Lenis automatic RAF or one project-managed RAF. When connected to the GSAP ticker, remove the extra loop, convert ticker seconds to milliseconds for `lenis.raf`, notify ScrollTrigger on Lenis scroll, and remove only the listeners and ticker callback this integration created before destroying the instance. Treat global ticker changes such as lag smoothing as project-wide decisions.
4. **Reduced motion includes JavaScript behavior.** Lenis 1.3.27 defaults respectReducedMotion to true: it disables smoothing and makes programmatic scrolling instant while keeping synchronization running, and it observes a live preference change without reload. It does not stop GSAP or copied component animations. Preserve the product's media state and define the visible static or simpler result for both initial and live reduced-motion states; verify the locked version before depending on this API.
5. **Exercise nested scrolling and navigation.** Define modal, side panel, code area, and iframe ownership. Background locking cannot block a modal's own scroll. In Lenis 1.3.27, choose deliberately among allowNestedScroll, the prevent callback, and scoped data-lenis-prevent attributes; automatic nested detection is convenient but checks the DOM path on scroll. Anchor handling is opt-in through anchors, so verify anchor offsets, hash changes, history return, wheel, touch, keyboard, and focus scrolling. Do not combine incompatible CSS smooth-scroll or snap behavior.
6. **Copied source still needs adaptation.** Inspect each component's dependencies, style scope, keyboard and touch behavior, screen-reader output, server rendering, and reduced motion. Different React Bits components may depend on GSAP, Motion, Three.js, or other packages. “Copyable” does not mean dependency-free or production-ready.
7. **Content availability is a product state.** For progressively enhanced content pages, meaningful HTML and links should be visible before decoration initializes. If the product requires JavaScript, state that requirement. On a low-performance target, measure and reduce the chosen implementation's cost rather than guessing devices or silently switching rendering strategies.

## Minimal joint-demo plan

This is a future validation plan, not a bundled or executed demo. In an authorized isolated React web page, use two content sections, one anchor link, one nested scroll panel, one Lenis instance, one transform-only GSAP/ScrollTrigger card, and one React Bits `FadeContent` TypeScript/CSS block. Keep the two animations on different elements and add no decorative 3D or template package.

The reviewed [FadeContent source](https://github.com/DavidHDev/react-bits/blob/4dc7b5b7772e1217c8fb8d2a7aa074302180e5b4/src/ts-default/Animations/FadeContent/FadeContent.tsx) reuses GSAP and ScrollTrigger. Its source starts with hidden visibility and samples reduced motion during its effect, so it needs project-specific treatment before it can satisfy pre-initialization visibility or live preference changes.

| Check | Exercise and pass condition |
| --- | --- |
| Scroll ownership | Wheel, trackpad, touch, PageDown/arrow keys, scrollbar drag, nested panel, anchor, and history return. No double smoothing, trapped nested scroll, or disagreement between DOM position, trigger region, and visual position. |
| Lifecycle | Scroll forward and backward, resize, route away, remount, and use React Strict Mode. No duplicate ticker, listener, timeline, or console error. |
| Reduced motion | Load with reduce enabled, then switch both directions at runtime. Content and controls stay visible and usable; large movement, blur, loops, and smooth pursuit stop according to the design. |
| Required content without decoration | For a progressively enhanced page whose content is expected from SSR or static HTML, disable JavaScript, reload, and verify text, links, and native scrolling remain available. Re-enable JavaScript and verify the enhanced path separately; do not claim this from an already hydrated SPA alone. |
| Target-device performance | Compare the same production build, viewport, device-pixel ratio, and scroll path against a baseline on an actual supported low-end device. Record frame-time distribution, long frames, main-thread work, and input response. CPU throttling is supplementary evidence. |
| Budget | Set the budget from the target refresh rate before testing; `16.7 ms` is only the nominal frame interval for 60 Hz, not a library guarantee. Reduce measured cost and retest when the target is missed. |

## Evidence boundary

The version and license facts above were rechecked against npm, GitHub releases and source, and the linked first-party license pages on 2026-11-08. No library, plugin, component, or external skill was installed; no demo was created; and no frame-rate or runtime behavior was measured for this repository.
