# Experience-led technology selection

Use this when a rendering, interaction, animation, sensing, or delivery-layer choice is actually needed. These are capability boundaries, not a package installation list. Check current official documentation for the chosen runtime's APIs, licensing, platform support, and deployment constraints before relying on them.

## Choose the target surface first

- **Web:** use semantic HTML/CSS/SVG for content, forms, accessible controls, and search-visible pages. Graphics layers must coexist with the product's navigable interface when both are required.
- **Mobile/native:** select native UI or the project's cross-platform runtime against gestures, lifecycle, accessibility, device integration, and delivery requirements. Do not apply web marketing-page rules to app flows.
- **Mini programs:** work within the actual platform's component, canvas, packaging, permission, and device constraints; use its installed development tools and verify on the intended surface.
- **Desktop:** account for windowing, keyboard workflows, OS integration, input devices, packaging, and the existing desktop runtime. Consider GPUIX only for a new native GPU-rendered React/Solid surface that can accept GPUI JSX/API and pre-1.0 constraints; its browser build is a separate Wasm/WebGPU-WebGL2 delivery, not the meaning of its desktop “no webview” claim.
- **Engine-led real-time 2D/3D:** consider Unity when the experience benefits from its scene, asset, interaction, and build workflow. Do not assume an Editor, license, build target, CLI, or MCP connection exists. Verify the required runtime and a real scene/test/build before claiming the toolchain works. Do not introduce an engine merely to animate conventional controls.

## Choose only the layers that serve the experience

| Capability needed | Candidate and boundary |
| --- | --- |
| Simple local UI transitions | Native CSS or Web Animations on web; corresponding native animation APIs on native surfaces. |
| OTP, verification-code, PIN, or short segmented-input feedback | Semantic form controls plus CSS and the Web Animations API. CSS owns resting, focus, error, and reduced-motion states; WAAPI owns interruptible fan/stagger and edge-lap effects. No new runtime dependency is needed. |
| React state, layout, presence, and gestures | Motion when it fits the React project. Do not impose React APIs on Vue/Svelte/native code. |
| Precisely sequenced timelines, scroll choreography, or coordinated DOM/SVG/canvas/3D animation | GSAP. Assign ownership of animated properties and lifecycle cleanup; use intentional sequences rather than motion for its own sake. |
| Scroll-driven narrative with generated keyframes/video, product transformations, or pointer-controlled media | `oil-motion` for concept contract, storyboard, Pilot, media budgeting/compilation, runtime mapping, and QA. External generation remains a separately authorized operation. |
| Designer-authored interactive vector assets | Rive when artboards and state machines are the appropriate asset/behavior workflow; verify the target runtime. |
| Stateful morphs between compatible stroke or filled icons | Morphicons when its target-framework integration fits. Preserve accessible button state and reduced-motion behavior, and inspect the selected pair's real geometry before adoption. |
| Motion inside one Lucide-style icon in React | Add only the chosen [Lucide Animated](https://github.com/pqoqubbw/icons) shadcn registry item, for example `npx shadcn@latest add "https://lucide-animated.com/r/activity.json"`. `@lucide-animated/<icon>` is a registry name, not an npm package. Inspect the exact component/export; it brings `motion` and expects registry conventions such as `@/lib/utils`. Confirm a new production dependency before adding it. Component code is MIT and retains its notice; the README permits personal/commercial component use but says the supplied tutorials/demos are available as-is and may not be redistributed or resold, so do not treat those materials as redistributable project assets. Add focus/touch/reduced-motion behavior beyond hover-only defaults. Use Morphicons instead when the requirement is a stateful stroke-glyph morph. |
| Interactive 3D scenes, viewers, cameras, lighting, and materials | Three.js; React Three Fiber when React scene composition improves the implementation. Use `3dviz-pro-max` for a grounded scene/explainer workflow and `img2threejs` for suitable reference-image-to-procedural-model work. |
| Playable browser 3D game | Three.js or the project's existing Three.js wrapper, with a game-state/simulation layer, input actions, camera, HUD, audio and an explicit QA seam. Prove one complete loop before content expansion. React may compose UI/scene structure but should not own every simulation sample. The external `threejs-game-skills` pack is an optional workflow/scaffold source, not a runtime requirement or proof of tests. |
| Generated game model, concept/texture, or audio asset | An explicitly selected provider pipeline such as Tripo, Gemini, or ElevenLabs only with authorization, credentials, current usage-rights review, provenance, and runtime-budget checks. Core Three.js gameplay and procedural/local assets do not require those keys. Generated meshes remain subject to scale/pivot/material/topology, animation/rig, loading, visual, and license acceptance. |
| High-volume interactive 2D graphics or sprite-heavy scenes | PixiJS when DOM/SVG is no longer the appropriate rendering model. |
| Low-level GPU rendering, custom pipelines, or compute | WebGL/WebGPU only when direct control is justified; otherwise select a suitable engine. Verify browser/device support for the chosen backend. For a WebGPU-specific workload, consult [typed WGSL and vgpu engineering patterns](webgpu-shader-notes.md); this is an optional candidate, not an installed runtime or a reason to replace an existing renderer. |
| Custom GPU materials, deformation, particles, simulation, or post-processing | Shaders when standard materials cannot express the goal. Match the language/abstraction to the selected engine and backend. |
| On-device perception of camera/image/audio/text input | MediaPipe Tasks when its current task and target-platform support match. Treat sensors and biometric-like inputs as privacy-sensitive boundaries; design consent and data handling before integration. |
| Browser-based 2D rigid bodies, collisions, or constraints | Matter.js. For 3D physics choose a runtime-compatible 3D engine, not Matter.js. |
| Agent-editable vector canvas, `.fig` conversion, or design-to-code handoff | [OpenPencil](https://github.com/ZSeven-W/openpencil) (MIT) when an editable JSON-based `.op` artifact, CLI/MCP canvas operations, or repeated frame/code export serves the workflow. Its implemented generators cover React, Vue, Svelte, HTML, Flutter, SwiftUI, Jetpack Compose, and React Native, but every output remains a scaffold requiring target-runtime review. |

<a id="aesthetic-web-effects"></a>
### Select an aesthetic web effect without adopting a six-library stack

Use this map when a brief asks for an “aesthetic web” treatment but the desired mechanism is still vague. It is a candidate-selection reference, not an installation list or a claim that visible source has a permissive license.

| Desired effect | Candidate and implementation boundary | Official source | License and adoption boundary |
| --- | --- | --- | --- |
| Freely explored immersive 3D site | React Three Fiber can compose a Three.js scene in an existing React product. The team still owns scene design, camera, navigation, loading, input, and accessibility; do not migrate a non-React product merely to adopt it. | [pmndrs/react-three-fiber](https://github.com/pmndrs/react-three-fiber) | [MIT](https://github.com/pmndrs/react-three-fiber/blob/master/LICENSE). Preserve the license notice, and review models, textures, audio, and other assets separately. |
| Text, button, pointer, or local hero interaction | React Bits is a selective source candidate: choose one exact effect and inspect its source, dependencies, focus/touch behavior, reduced motion, and output rights. Reuse the existing [React Bits selection note](gsap-lenis-react-bits.md). | [DavidHDev/react-bits](https://github.com/DavidHDev/react-bits) and [reactbits.dev](https://reactbits.dev/) | Its [MIT + Commons Clause terms](https://github.com/DavidHDev/react-bits/blob/main/LICENSE.md) allow use in an application, site, or product. They prohibit selling, sublicensing, or redistributing the components, tools, or sounds themselves—alone, bundled, or ported—and prohibit offering the tools or a substantially similar copy as a hosted service. Exports may be used in a product but not sold or redistributed on their own or as the product, such as a sound, texture, background, or template pack. Treat it as a custom-license source candidate, not a permissive component bundle. |
| Liquid-metal logo | Liquid Logo is a material-effect candidate for an existing mark; preserve the logo's recognition and do not infer its terms from another repository by the same organization. | [paper-design/liquid-logo](https://github.com/paper-design/liquid-logo) and [liquid.paper.design](https://liquid.paper.design/) | [PolyForm Shield 1.0.0](https://github.com/paper-design/liquid-logo/blob/main/LICENSE) excludes products that compete with the software or with products the licensor provides using it. Review the terms for the intended use before adoption. |
| Refractive glass control or surface | Liquid Glass JS is a WebGL candidate. First use the [glass-mechanism selector](#select-glass-materials-by-mechanism) to decide whether refraction is actually required; a native material or CSS backdrop may be the smaller route. | [dashersw/liquid-glass-js](https://github.com/dashersw/liquid-glass-js) | [MIT](https://github.com/dashersw/liquid-glass-js/blob/main/LICENSE). Its current README still lists npm packaging, React/Vue wrappers, accessibility improvements, and mobile touch optimization on the roadmap, so source availability does not establish production readiness or cross-browser behavior. |
| Flowing color field or art-directed background | ShaderGradient is a candidate for React/Framer-oriented gradient rendering. Inspect the selected package and peer dependencies, and keep the background subordinate to readable content. | [ruucm/shadergradient](https://github.com/ruucm/shadergradient) and [shadergradient.co](https://shadergradient.co/) | The repository currently has no root license metadata/file while its [README states MIT](https://github.com/ruucm/shadergradient#license). That README statement is evidence to investigate, not proof that every package, asset, or version has a complete redistributable license; confirm the exact material before commercial adoption. |
| Dependency-light canvas shader, texture, or mask effect | Paper Shaders separates a vanilla JavaScript core from framework adapters. Choose the smallest compatible layer; “zero dependencies” does not mean zero GPU cost or automatic framework compatibility. | [paper-design/shaders](https://github.com/paper-design/shaders) and [shaders.paper.design](https://shaders.paper.design/) | [Apache-2.0](https://github.com/paper-design/shaders/blob/main/LICENSE). Preserve the required notices and do not extend this license to Liquid Logo. |

Choose from the brief, not from the catalog. One hero effect may be enough; two can be appropriate when each serves a named content or interaction purpose, but all six are never a target. For every selected effect, state the content purpose, trigger, controlled subject, resting state, and reduced-motion state. Keep the existing framework, brand system, and component semantics when they still fit, and prefer CSS or SVG when they can deliver the same experience.

Give each animated property, scroll progress value, render loop, and lifecycle one owner. Verify keyboard, touch, focus, text contrast, loading, and reduced motion, then measure frame time and resource cost on the target devices. A selection decision is not performance or visual acceptance.

Source inspiration is credited to @恒瑞的人生实验室. The six official repositories and the linked license or README evidence above were checked on 2026-11-23. This review did not inspect the demos visually, install dependencies, build the libraries, or copy their code or media into a product.

<a id="card-carousel-selection"></a>
### Select the card-browsing form before the effect

Start from what the user is doing, then preserve the project's existing component, renderer, and stateful gesture-settlement rules.

| Task and content | Form and boundary |
| --- | --- |
| Image-led portfolio, gallery, or product hero where near/far depth is part of the presentation | A ring-depth carousel is a candidate when it has enough display area and the target devices can render it. `22` cards is the supplied demonstration workload, not a universal maximum. If an optional `kubai-ring-cards` skill is actually available, read it only after this form is selected; it is not bundled here. |
| Recommendations, related images, or a sequence where order and readable text matter more than spatial drama | Prefer an ordinary horizontal scroller or carousel with explicit previous/next navigation. Reuse the existing component instead of introducing a ring renderer. |
| Precise finding, filtering, or multi-item comparison—especially prices, specifications, or dense administration data | Prefer a grid, list, or comparison table. More than `30` items is a prompt to reassess browsing cost in the supplied brief, not an automatic layout switch. |

A visual ring does not make the logical reading order circular. Keep stable item identity and order, a readable current-item name, previous/next controls, keyboard access to the ring and any exposed settings, and no duplicate invisible cards in the accessibility tree. If the product adds automatic rotation, provide stop/resume and pause it for focus and hover as applicable; use the [WAI carousel pattern](https://www.w3.org/WAI/ARIA/apg/patterns/carousel/) as a semantics and control reference, not as proof that the visual implementation is accessible.

#### Demonstration starting values

Use these only when reproducing the supplied ring-depth direction. They are adjustable starting values, not platform limits or requirements for ordinary carousels.

| Parameter | Starting value | Interpretation and correction |
| --- | --- | --- |
| Inside perspective | `860px` | One of two view-specific perspective values. With the source projection `P / (P - z)`, a smaller `P` creates stronger perspective; it does not make the scene flatter. `600px` was a source-panel lower bound, not a universal safe value. See [MDN perspective](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/perspective#description). |
| Outside perspective | `1500px` | Keeps the outside ring visually gentler than the inside view; verify the relation at the real frame size. |
| Glass rim | `160px` on each side; `25%` dispersion | Wider rims consume more content. Treat the percentage as source tuning, not a physical material constant. |
| Outside depth | maximum `14px` blur; `50%` far fade | Blur increases as cards move away from the focus region. The source fade mixes toward the page background; it is not equivalent to setting card alpha to `0.5`. |
| Cards | `180 × 300px`, `18px` gap, `22` cards | Workload and rhythm from the demonstration, not universal geometry or a hard count ceiling. |
| Fluid flow | `20%` | A source slider value for gradient motion, not a normalized performance measure. |
| Continuous corner | `32px` | A source corner radius. It does not mean the card outline should deform arbitrarily with the ring radius. |

The source brief's warnings above `20px` blur or below `35%` fade are visual tuning cues, not readability or performance laws. The source control model has seven parameter classes: Perspective (two view-specific values), Glass rim, Dispersion, Flow, Corner, Depth blur, and Far fade. It exposes five rows in each view because Perspective differs by view and several controls are shared. Do not reproduce an inconsistent “six controls” label or force the panel into a production surface when it is only a development aid.

#### Implementation contract

- Preserve one set of card identities while a signed curvature moves through the expanded state between inside and outside views. Do not rebuild two unrelated carousels or instant-swap them. Keep the selected renderer's drag, release velocity, snap, bounds, and new-input-interrupts-old-motion rules. Preserve its near-eye clipping and verify a valid depth range at the target frame sizes so `P - z` does not approach or cross zero and invert the projection.
- For the full glass rim, render the cards into a texture, then apply bounded edge displacement and chromatic sampling. A clip or mask constrains pixels but does not create refraction. Inspect for fold-back, repeated cards, seams, and color separation that obscures content.
- In the outside view, keep the center clear and increase blur/fade with distance. The source renderer uses per-pixel coverage, card margins, and image mipmaps; a `backdrop-filter` over moving content is not equivalent and can shimmer.
- Preserve the front/back image direction. The source turn is an `1800ms` overall progression with nonlinear lag based on arc distance. A separate `40–80ms` stagger suggestion is a different timing model; do not layer the two or claim they are equivalent.
- In reduced motion, stop fluid motion and card flipping and present a clear static destination while retaining view switching, navigation, and card access. Do not freeze the interface or silently substitute a simplified CSS renderer when the selected GPU path is unavailable; a renderer change is a new technical decision.
- Measure the actual device, frame, pixel density, and card content. The source's `60fps` target and instruction to reduce blur below `45fps` are unverified tuning notes, not current-project evidence or permission for automatic quality degradation. If the selected route misses its target, identify the bottleneck and adjust only within the approved design.

#### Acceptance for the ring-depth route

- At the demonstration defaults, the inside composition shows the intended five-card rhythm and the outer cards approach the glass without folds, repeated cards, or gaps. Other frames use their selected composition rather than forcing five items.
- Changing inside/outside view bends the same card set continuously. Reversing or interrupting the change preserves identity and settles on a valid view without a jump.
- The outside focus region stays clear; blur increases with distance up to the selected maximum, far fade mixes toward the actual page background, and no hard blur edge or shimmer appears while cards move.
- Card backs remain correctly oriented. If a turn sequence is used, it progresses from the selected center relationship and can reverse or be interrupted without combining incompatible stagger systems.
- Every exposed control updates the intended parameter and reset restores the documented values. The logical current item, focus, screen-reader order, keyboard and touch navigation, light/dark background behavior, and reduced-motion presentation remain valid.
- Verify real frame time rather than inheriting the source's target. Ordinary motion and reduced motion are separate acceptance states.

This is an independently written selection and engineering synthesis based on a supplied ring-card brief credited to @kubai087. No demonstration source code, screenshots, videos, card images, or fluid-gradient assets are included; their redistribution rights were not established. Use project-owned or separately licensed media, preserve any notices on reused code, and inspect an optional specialist's current source and terms before adaptation.

### 3D asset creation, viewing, and delivery

Keep creation, display, and handoff as separate boundary decisions:

- **Creation route:** `img2threejs`-style work reconstructs editable Three.js assets from reference images; a generative provider (e.g. Tripo) targets a usable mesh with optional auto-rigging/animation and engine exports (FBX/GLB). Choose by how much post-generation editability the target needs, not by provider fashion. Provider defaults, view counts, quality tiers, and polygon caps change between versions, so read the provider's current official limits instead of copying one tutorial's numbers.
- **Reference consistency:** choose from what the target can express programmatically, required editability, shape complexity, and the availability and consistency of real multiview evidence. Neither procedural reconstruction nor a generative mesh guarantees fidelity. A multiview route still needs mutually consistent views — same subject, proportions, palette, and pose — and one view cannot resolve hidden sides, so supply missing angles and validate the resulting model against them.
- **Pose and rigging:** read the selected rigger or API's current input contract before creating the asset. Some require or benefit from a T-pose or A-pose with limbs clear, and the target animation set may impose a skeleton or rest pose; use those actual requirements rather than a universal pose rule. A DCC workflow can re-pose, rebuild, or rebind later, but that may require redoing skinning and weights, so treat pose mismatch as rework cost rather than impossibility.
- **Whole vs parts:** choose partitioning from deformation, authoring/swapping, material, draw-call, and culling needs. Static geometry may be merged when those budgets support it; animation does not automatically require separate objects, because a continuous skinned mesh can deform, while independently moving rigid parts may need their own hierarchy.
- **Topology and budget:** derive density and topology from the target runtime instead of a universal polygon count — the lightest glTF/GLB that holds the shape for web/AR, the engine's own conventions for games, a watertight mesh for print — and treat any single “good” triangle count or decimation limit as tool- and version-specific.
- **Delivery layer:** [model-viewer](https://modelviewer.dev/) is a display/interaction layer for glTF/GLB, not an authoring tool. On the web it renders glTF/GLB only; a USDZ-only source shows no model, because USDZ belongs to AR Quick Look rather than web display. It loads DRACO, KTX2/Basis, and Meshopt compressed glTF through decoders that load on demand, so weigh decoder size against the file savings. It plays glTF animations (`autoplay`, `animation-name`, speed, crossfade, simultaneous clips), supports posters and capture of the current render to a canvas/blob image (`idealAspect` for a poster-matched aspect), and hands off to AR — WebXR (default; needs HTTPS and `xr-spatial-tracking`), Scene Viewer, or Quick Look with auto-generated USDZ; use `ios-src` (`.usdz`/`.reality`) when the auto-generated USDZ is not adequate, and note that auto-generated USDZ does not support animations yet. It scales render resolution to hold frame rate; decide whether auto-rotation is affordable from measured frame time on target devices rather than disabling it from model complexity alone. It complements rather than replaces img2threejs-style procedural reconstruction: authoring vs shipping.

### Choose a 3D production route

- Use `3dviz-pro-max` when the deliverable is an authored scene, explainer, spatial puzzle, or interactive model whose subject, representation, camera, materials, and behavior need to agree. Search its catalog only for the unresolved decision, copy any selected scaffold or kit into the project before installing project dependencies, and inspect real frames. A valid skill or successful catalog query proves discovery, not rendering or visual quality.
- Use `img2threejs` when one object or character reference should become editable procedural Three.js geometry. Use an existing licensed mesh or the project's asset pipeline when it already fits better.
- Consider [Image Blaster](https://github.com/neilsonnn/image-blaster) when the input is one scene photograph and the intended upstream result is a layered world: a static Gaussian-splat environment (`.spz`), separately addressable object meshes (`.glb`/`.obj`), and ambient or event sound (`.mp3`). Keep stable object IDs, coordinate frame, world scale, units, origins, and asset provenance in one manifest before parallelizing independent object or audio work. A splat is appearance data, not collision, navigation, occlusion, or semantic truth; author and verify the geometry or proxies those behaviors need.
- Image Blaster is an MIT-licensed Claude skillset, not an installed Codex runtime. Its documented full generation path uses World Labs and FAL services and named image, mesh, world, and sound models. Repository licensing does not establish provider cost, input privacy, or generated-output rights. Call a selected provider only with explicit authorization, configured credentials, and current terms; otherwise stop at scene decomposition, the asset contract, prompts, and integration skeleton. The project's “under five minutes” statement is a project claim, not a delivery estimate or acceptance result.
- On integration, load the real target scene and inspect registration between splat and meshes, scale and pivots, depth/occlusion, collider and navigation ownership, PBR and lighting consistency, audio loop/event binding, load size, frame time, input, and accessible DOM/native controls. Separate assets produced from frames actually observed.

### Select glass materials by mechanism

Use the target surface's material model rather than treating every translucent panel as the same effect:

| Desired mechanism | Preferred route and boundary |
| --- | --- |
| Native frosted/vibrant surface | Use the current platform's material or vibrancy API inside its existing UI stack. Verify appearance against real window content, active/inactive state, light/dark mode, increased contrast, and reduced-transparency settings; another platform's glass language is not a migration reason. |
| Web glassmorphism or frosted layer | Use a controlled translucent fill, `backdrop-filter` blur where the target browser supports it, restrained border/highlight and inner/outer shadow or gradient. Keep the effect local and test scrolling/compositing cost; backdrop blur softens pixels behind the element but does not refract them. |
| Actual liquid edge or refraction | Use a defined distortion/displacement mechanism in the selected native renderer, SVG/filter pipeline, canvas, WebGL/WebGPU, or shader stack. State what bends, its displacement bounds, and who owns motion. Do not label plain blur or a scaled backdrop as physical refraction. |
| Figma direction or simulation | Layer blur, mask/distortion, highlight, and text to communicate the intended material, then reselect the mechanism for the real runtime. A convincing design-file stack is not runtime proof. |

- Use blur to establish depth only when foreground content stays sharp and the background has enough structure to reveal separation. Avoid nested glass surfaces that compound blur and transparency; spacing, solid grouping, and hierarchy still carry the interface. In dashboards, alerts, freshness, live state, data and actions outrank glass—see [dashboard composition](dashboard-composition.md).
- Derive tint, opacity, border luminance, shadow, noise and type treatment from the actual background and contrast requirements. Archived Figma demonstrations include blur around `40–60`, a `20%` white fill, a `0 8 24 / 15%` shadow, dual blur around `20 + 80`, and a separate `1%`-fill liquid-glass stack with radial strokes and multiple inner shadows. These are specimen readings, not defaults or a requirement to reproduce every layer.
- If foreground ink or glass luminance adapts to the content underneath, define and test that mapping across real extremes; never let moving imagery make text, focus, charts, or status illegible. Prefer a controlled surface/tint when reliable sampling is unavailable. Treat reduced transparency as a designed more-opaque state and keep content hierarchy intact.
- Route scroll-owned edge highlight, luminance, and distortion through [the existing Liquid Glass motion vocabulary](motion-description-vocabulary.md#liquid-glass). Give each animated property one owner, keep reverse motion coherent, and provide a composed reduced-motion still rather than making readability depend on movement.
- Inspect real light/dark backgrounds, focus and interaction states, platform accessibility preferences, clipping at rounded corners, scrolling, resize, and target-device frame time.

### Select OpenPencil, Figma, or direct code

- Use OpenPencil for a versionable agent-editable canvas, `.fig` conversion, headless/batch canvas work, or repeatable multi-target handoff when the actual `op` binary or MCP surface is available. This selection refers to `ZSeven-W/openpencil` / `op.zseven.tech`, not the separate project at `openpencil.dev`.
- Keep Figma when the organization depends on its shared component libraries, comments, prototypes, permissions, plugins, or established review flow. A supported `.fig` importer does not prove lossless parity or round-trip editing.
- Prefer direct code when an established product implementation is already the source of truth, the requested change is bounded, or semantics, responsive runtime behavior, data, and application state matter more than an intermediate canvas artifact.
- Before writes, verify the selected surface: on the CLI path run `op status` and `op tools`; on a direct MCP path use equivalent connection/ping, tool discovery, and read-only layout calls without requiring a CLI binary. Inspect the target file and layout when one already exists; for a new draft, use an explicitly chosen blank document after readiness passes. Do not hard-code the default port as proof of availability. After authorized edits, export the affected frame/page or chosen code target and inspect it in the real target runtime; code generation is not production acceptance.
- Treat provider-backed AI as a separate data and authorization boundary. A local `.op` document and deterministic MCP operations do not imply that prompts/assets remain local or authorize a configured provider call.

### Evaluate GPUIX as a pre-1.0 candidate

[GPUIX](https://github.com/remorses/gpuix) (Apache-2.0) batches React/Solid mutations into a Rust `RetainedTree` that GPUI rebuilds and paints through Metal, DirectX, or Vulkan; layout, text, and input are GPUI elements rather than DOM. Keep the selection bounded:

- exact-pin the selected adapter (`@gpuix/react` or `@gpuix/solid`) and `@gpuix/native` as direct dependencies and upgrade them together; `@gpuix/cli` publishes independently and is not part of that lockstep pair;
- prove the real target OS, input, text, accessibility, automation, packaging, and update path with a runnable spike; advertised platform support is not local acceptance, and at the 2026-09-24 official snapshot Linux lacks the headless test renderer used on the other native targets;
- evaluate the browser path separately: it needs Wasm plus matching tooling, cross-origin isolation headers, and observed WebGPU or WebGL2 behavior; a working native build proves none of those conditions;
- preserve Electron or Tauri when the product depends on DOM/webview compatibility or its established packaging and integrations. GPUIX is not an automatic migration or superiority claim.

## Implement continuity-driven interaction

- Use the target framework's shared-layout support, native layout-animation APIs, or a FLIP-style measurement when an object keeps its identity while position, size, or radius changes. Keep stable keys/identity and animate one rendered object rather than swapping two complete layouts.
- Keep high-frequency pointer, drag, scroll, tilt, and highlight values in animation/runtime values or the platform gesture system. Commit application state at meaningful transitions; do not rerender the whole component tree for every input sample.
- Model multi-stage interactions as explicit states and transitions. Timelines may orchestrate ordered phases, but semantic state owns pending, success, selection, commit, and cancel. Cleanup or cancel animation work when the component leaves or a new transition supersedes it.
- Assign each animated property to one owner. GSAP, Motion, CSS/native animation, Rive, Three.js, and gesture code may cooperate across separate layers, but two systems must not independently write the same property.
- Use ordinary transforms, perspective, masks/clipping, gradients, SVG path drawing, and spring/layout APIs before reaching for a canvas, shader, physics engine, or 3D engine. Select a heavier renderer only when the experience actually needs its capability.

## Select advanced interaction techniques

Map a named technique from the [Advanced Interaction Techniques](../SKILL.md#advanced-interaction-techniques) table to the lightest layer that preserves it, then implement from the recorded reference parameters instead of guessing thresholds. For a single-loop participatory site, also read [Design playable, shareable micro-sites](../SKILL.md#playable-shareable-micro-sites): its sample is a visual/play-loop reference, not a technology or engagement claim.

| Technique | Preferred layer and boundary |
| --- | --- |
| FAN, PARABOLA, COLLAPSE | CSS transforms and `transform-origin`, or WAAPI / scroll-linked CSS properties when scroll drives them. Use independent channels or a supported motion path for a genuine curve; one owner per property. Derive geometry such as `(W - W * S) / 2` from measured size. |
| INERTIA, SHEET, STICKY | Platform gesture recognizer or Pointer Events plus one `requestAnimationFrame` loop holding velocity/displacement in animation values. Integrate decay against elapsed time, keep inertia and snap ordered, and commit sheet/sticky state at the stated threshold. |
| REORDER, FLIP | Measured FLIP/shared-layout with `transform`; preserve stable keys and focus order during drag, commit the logical/semantic order afterward, and release an inverted FLIP state only after the target runtime has committed it. |
| STROKE | Pointer Events with `getCoalescedEvents` where supported and a canvas or SVG path; sample in the event handler, keep geometry/rendering in one loop, and clamp calculated width to a positive range. |
| Page transition | The platform's view/page-transition API or two layered surfaces with coordinated outgoing recession/dimming and incoming motion. Define the source/destination geometry, coverage/commit point, focus transfer, reverse/interruption behavior, and reduced-motion state rather than freezing the old surface as an unrelated sticker. |

These map onto the continuity rules above and do not justify a new runtime dependency. Preserve follow/threshold/snap for drag, selection, and release-settlement interactions; for click/stroke/page transitions verify their actual trigger, path or feedback, terminal state, reverse/interruption behavior, and designed reduced-motion state.

## Select OTP and segmented-input motion

Default to native form controls, CSS, and WAAPI. Let the framework own code value, validation state, and the verification request; do not rerender on animation samples. Let CSS own stable visual states and `prefers-reduced-motion`, and give WAAPI exclusive ownership of transient transforms so paste, autofill, correction, and unmount can cancel or retarget cleanly.

Use an SVG outline only as a decorative per-slot layer. A `rect` normalized with `pathLength="1"` makes one edge lap straightforward with dash values while leaving the input, label, focus, status, and submit behavior in ordinary DOM semantics. Do not add GSAP, Motion, canvas, or a component package solely for this recipe; reuse an existing project runtime only when it already owns the same interaction layer without property conflicts.

## Select scroll-driven motion and delivery

For GSAP timelines, Lenis smooth scrolling, or React Bits source candidates, read [GSAP, Lenis, and React Bits selection](gsap-lenis-react-bits.md). Choose the three independently: that reference records a dated version and license snapshot, one-loop ownership, cleanup, reduced-motion and nested-scroll checks, and an unexecuted demo plan. It does not make any library mandatory or prove that one is installed in the target project.

Choose the lightest layer that can preserve the intended change:

| Experience | Layer and boundary |
| --- | --- |
| Text, layout, opacity, transforms, masks, or SVG drawing tied to scroll | Native scroll-driven CSS where the project/browser target supports it, or the existing animation layer. Use GSAP for coordinated multi-stage choreography; keep semantic state outside the timeline. |
| Pre-rendered cinematic journey whose frame must follow scroll | A seek-optimized H.264 MP4 plus one persistent `HTMLVideoElement` and a frame-scrub controller. Scroll selects `currentTime`; the video owns camera and semantic motion. Use `oil-motion` when asset generation, chaining, compilation, or media budgeting is required. |
| Camera, geometry, lighting, or material changes in a real-time scene | Three.js/R3F and shaders as needed. Drive one normalized progress value into the scene loop; do not make React rerender the scene on every scroll event. |
| Generated semantic transformation, complex occlusion/contact, or cinematic camera chain | `oil-motion` media workflow. Lock keyframe states and continuity, then let its budget choose baked video, chroma video, or an alpha atlas independently from the runtime controller. |
| Pointer-following avatar, product, or scene | First classify the parameter space as linear, circular, or two-dimensional. Use deterministic geometry when sufficient; use sampled/generated media only when the poses themselves require semantic generation. |

Choose the scroll driver independently from the video format:

- **Custom progress plus `requestAnimationFrame`:** use when one local stage only needs normalized scroll progress mapped to video time. It is the smallest no-dependency route; the scroll handler records a target and one frame loop owns seeking.
- **GSAP ScrollTrigger:** use when the project already uses GSAP or needs coordinated pinning, named ranges, responsive refresh, and synchronized DOM/SVG choreography. `scrub: true` follows scroll directly; numeric scrub adds intentional catch-up. Feed its progress into the single video-seek owner, register the plugin, and clean up the trigger with the component lifecycle.
- **CSS/WAAPI scroll timelines:** use for supported CSS properties and compositor-friendly overlay motion when the target browser matrix allows it. `ScrollTimeline` is not universally available, and CSS `animation-timeline` cannot set `HTMLVideoElement.currentTime`; video seeking still needs JavaScript. Do not introduce a dual implementation merely to claim native support—select the route that covers the actual target browsers and experience.

For every route, distinguish three concerns:

1. **Navigation:** how the page moves—continuous document scroll, sticky section, or paged sections.
2. **Time control:** continuous scrub, threshold-triggered segment playback, or autonomous playback.
3. **Delivery:** DOM/SVG, real-time canvas/WebGL, sprite atlas, chroma video, or baked video.

Do not infer one from another: a paged section can scrub a continuous asset, while ordinary scrolling can trigger self-playing segments. Define local scroll ranges and stable state anchors; input callbacks update a target, and a single animation/render loop applies the latest value. Generated-media timing must come from the compiled asset manifest rather than duplicated constants in components.

Before choosing generated media, separate semantic motion from deterministic geometry. Whole-layer position, scale, rotation, clipping, paths, camera transforms, lighting parameters, and text overlays belong in code. Identity-sensitive articulation, structure/material transformation, contact, and occlusion may justify generated keyframes/video. Lock whether the background belongs to the page or the media, and produce native desktop/mobile aspect ratios from the real container instead of relying on a universal `1:1` source.

External image/video generation requires an explicitly authorized provider and configured credential. If the task needs new generated assets and either is absent, deliver only the concept contract, storyboard, keyframe and prompt plan, asset manifest, and implementation skeleton; do not call the provider. Existing user-supplied video or frames can still pass through deterministic analysis, Pilot, budgeting, compilation, and runtime integration without a model credential. Install `oil-motion` Python requirements only when one of those media-production routes is selected.

Reduced motion and the pre-media loading composition are explicit designed states. A provider, decoder, WebGL, or resource failure must release interaction locks and surface the error; it does not authorize an automatic provider, format, or static-media fallback. Any route change is a new production decision governed by the user brief and project rules.

## Select and construct loading indicators

Choose the indicator from the information available to the user, then choose its rendering form:

| Need | Preferred form and boundary |
| --- | --- |
| Measurable completion | Determinate native or project progress component driven by real progress. Do not present invented percentages. |
| Known content structure | A restrained skeleton matching the final geometry; do not skeletonize unrelated controls or keep it after content settles. |
| Short, local, indeterminate wait | The project's existing spinner or a self-contained CSS/animated SVG indicator. Do not add an animation runtime only for a decorative loader. |
| Host-controlled color, motion, or semantics | Inline SVG using `currentColor`, CSS custom properties, and `prefers-reduced-motion`. Scope IDs and styles when several copies share a document. |
| Isolated reusable asset | External SVG through `<img>`, CSS background, or `<object>`. Its own CSS animation can run without JavaScript, but host styling is limited, so select or provide the correct light/dark file explicitly. |

Reusable SVG construction patterns:

- **Radar sweep:** approximate a conic tail with `N` angular wedges whose opacity changes across the sweep. Derive each blip's animation phase from its polar bearing, modulo one rotation, so it flares as the leading edge crosses rather than on an unrelated timer.
- **Projected ring:** a side-view circle projects to horizontal radius `R * abs(cos(t))`. Animate an ellipse's `rx` from `R` to `0` and back, or apply the equivalent centered x-scale, to make a gyroscope ring turn through edge-on without fake opacity. Nested groups can counter-rotate or undo the parent plane's squash when a bead must remain circular on an elliptical orbit.
- **Seamless tide:** draw an integer number of identical wave periods beyond the clipped viewport, then translate the path by exactly one period. The start and end phases must match; arbitrary path length or travel distance creates a seam.
- **Geometry carries the effect:** prefer a real eccentric arc/pivot for iris-like blades and put visual mass at a moving trail's leading edge for cascade-like motion. Derive the motion from the shape or phase relationship before adding easing or filters.

[Circle Loaders](https://circleloaders.dominikakissi.com/) is a reference source for these patterns and for copyable standalone SVGs. When adapting one, keep the smallest chosen asset, expose intentional color/tempo/diameter controls, retain its reduced-motion still frame, verify its current license, and inspect it on the actual background and target size.

## Decision and acceptance

For a material choice, state the desired capability, chosen layer, important cost/constraint, and how it will be verified. Use the project's existing package manager and architecture. Preserve a working stack unless a concrete requirement warrants changing it; obtain any additional authority needed for migration or new production dependencies.

Judge the result against the actual target devices and inputs, accessibility and reduced-motion needs, asset workflow, loading/bundle/runtime costs, and relevant measured frame-time or interaction budgets. A small scoped edit does not need a new benchmark suite or architecture memo.
