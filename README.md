# Frontend Experience

`frontend-experience` is an instruction-only Agent Skill for designing, implementing, and verifying substantial client experiences across web, mobile, Mini Programs, desktop, and real-time 2D/3D.

It helps an agent turn product intent into a working interface by making five decisions explicit:

1. what the user is trying to complete;
2. which visual and interaction direction fits that task;
3. which rendering layer and technology fit the target surface;
4. which states, interruptions, and accessible paths must exist; and
5. what must be observed in the real runtime before the work is accepted.

The skill does not impose a house aesthetic, framework, component library, or animation library. It preserves a working project stack unless a concrete capability requires a change.

## What is included

- [`SKILL.md`](SKILL.md): the core workflow and its routing rules.
- [`references/technology-selection.md`](references/technology-selection.md): rendering, 2D/3D, motion, canvas, media, and interaction-layer choices.
- [`references/motion-description-vocabulary.md`](references/motion-description-vocabulary.md): turns conversational motion language into testable behavior contracts.
- [`references/component-motion-tokens.md`](references/component-motion-tokens.md): maps component transitions to semantic motion tokens.
- [`references/dashboard-composition.md`](references/dashboard-composition.md): composition patterns and acceptance checks for dense data surfaces.
- [`references/profile-card-layouts.md`](references/profile-card-layouts.md): twelve content-led profile composition patterns.
- [`references/reactdrops-component-patterns.md`](references/reactdrops-component-patterns.md): source, license, dependency, and runtime checks for selective ReactDrops reuse.
- [`references/responsive-typography.md`](references/responsive-typography.md): semantic, fluid, and language-aware type-system guidance.
- [`references/safe-area-layout.md`](references/safe-area-layout.md): safe-area ownership for web, hybrid, and native layouts.
- [`references/six-popup-types.md`](references/six-popup-types.md): task-led selection and semantic contracts for six popup and overlay patterns.
- [`references/six-app-interactions.md`](references/six-app-interactions.md): six connected action-feedback and stateful-motion patterns.
- [`references/six-component-interactions.md`](references/six-component-interactions.md): six stateful app and Mini Program interaction recipes.

There are no scripts, runtime packages, generated assets, model credentials, or required MCP servers in this repository. The core workflow works with ordinary file inspection, editing, the project's existing toolchain, and direct runtime observation.

## What comparable results require

Installing the skill supplies the decision process, interaction contracts, technology selection rules, and verification standard. It does not supply a brand, product requirements, source assets, application data, a running simulator, or visual taste specific to your product.

To apply the worked recipes and target comparable interface quality, provide:

- the repository or editable project;
- the target surfaces and representative viewport or device sizes;
- the primary user task and completion condition;
- real copy, representative data, and available assets;
- brand or existing design-system constraints;
- required states such as loading, empty, error, pending, success, and permission-denied;
- supported input modes such as keyboard, touch, pointer, controller, or assistive technology; and
- a runnable target for visual and interaction verification.

The skill aims for comparable design discipline and runtime evidence. It cannot promise identical pixels across different fonts, assets, browsers, devices, rendering engines, or project constraints.

## Install in Codex

Current OpenAI documentation defines a skill as a directory containing `SKILL.md` and optional `references/`, `scripts/`, and `assets/`. Codex discovers repository skills under `.agents/skills` and personal skills under `$HOME/.agents/skills`. It can also install a skill from another repository through `$skill-installer`. See [OpenAI's Build skills documentation](https://learn.chatgpt.com/codex/build-skills).

### Install with the skill installer

Ask Codex:

```text
Use $skill-installer to install the frontend-experience skill from
https://github.com/eonpaper123/frontend-experience.
```

If the new skill does not appear, restart Codex as described in the official documentation.

### Install for one repository

Copy this repository into:

```text
<repository>/.agents/skills/frontend-experience/
```

The resulting path must contain `SKILL.md` directly:

```text
<repository>/.agents/skills/frontend-experience/SKILL.md
```

This is the useful layout when the workflow should travel with a project. Commit the copied directory or add this repository as a Git submodule only if that matches the project's dependency policy.

### Install for one user

Copy this repository into:

```text
$HOME/.agents/skills/frontend-experience/
```

Use the platform's normal home-directory expansion. Do not place secrets or project-specific acceptance evidence inside the shared skill.

## Use in other coding agents

This repository follows the portable Agent Skills shape: one directory rooted at `SKILL.md`, with supporting Markdown under `references/`. A host that supports Agent Skills may discover it through its documented skill location.

For a host without documented skill discovery, give the agent the repository and say:

```text
Read SKILL.md as the workflow for this task. Load only the references it routes
to. Follow the current project's instructions and existing design system first.
Implement the requested experience, then verify it on the actual target surface.
```

That is manual context loading. This repository does not claim automatic discovery or installation behavior for other hosts.

## Invoke the skill

In Codex, mention the skill explicitly when you want to force the workflow:

```text
Use $frontend-experience to redesign this checkout flow for mobile and desktop.
Preserve the current framework and payment contract. Implement the smallest
complete path and verify keyboard, touch, error, pending, success, and reduced-
motion behavior in the real app.
```

Codex may also invoke it implicitly when a request matches the description in `SKILL.md`.

Do not invoke it for a typo, a one-property styling fix, an isolated backend task, or a request that only asks for analysis. The skill deliberately scales down for bounded changes and does not turn every UI edit into a redesign.

## Core workflow

### 1. Read the real task and existing product

Inspect the applicable project instructions, current interface, existing components, design tokens, routes, state model, assets, and validation commands. Name the primary user task and completion condition. Preserve unrelated behavior and user work.

### 2. Establish one direction

Write a short design read covering:

- audience and primary task;
- target surfaces and input modes;
- hierarchy and visual traits to preserve;
- required states and recovery paths;
- asset strategy;
- interaction language; and
- observable acceptance.

Use the existing design system when it still serves the task. A new skill, library, or visual reference is not a reason to replace a working stack.

### 3. Select the lightest capable implementation layer

Read [`technology-selection.md`](references/technology-selection.md) only when a real technology choice exists. Prefer, in order:

1. the project's existing component or pattern;
2. a platform feature or standard API;
3. an already-installed dependency; and
4. a new dependency only when the capability justifies it and the project permits it.

Keep one owner for each animated property or state transition. Do not let CSS, a motion library, and a gesture handler fight over the same transform.

### 4. Build the smallest complete slice

Reach one usable path early. Include every state needed to complete that path, including authoritative pending/success/error feedback where the product requires it. Keep state in the project's existing source of truth.

For motion, define source, destination, anchor, commit/cancel threshold, interruption behavior, reverse path, and reduced-motion result before choosing keyframes or springs.

### 5. Verify the actual experience

Exercise the primary path on the target runtime. Inspect relevant desktop and mobile sizes, supported input methods, loading and failure states, interruption and reversal, focus order, screen-reader status where applicable, reduced motion, and the relevant app or window lifecycle.

A build, screenshot, generated component, static HTML file, or passing unit test is narrow evidence. None alone establishes that the delivered experience is usable.

## Reference selection map

| Task signal | Load | Output expected |
| --- | --- | --- |
| Dashboard, analytics, operations console, dense admin surface | [`dashboard-composition.md`](references/dashboard-composition.md) | Decision-led hierarchy, representative data states, density and navigation acceptance |
| Profile, team, speaker, or personal card composition | [`profile-card-layouts.md`](references/profile-card-layouts.md) | A layout selected by content priority, not by decorative preference |
| Distinctive React hero, portfolio feature, product card, or agent-state visual with no suitable project component | [`reactdrops-component-patterns.md`](references/reactdrops-component-patterns.md) | One source-verified candidate, dependency and custom-license boundary, project-specific adaptation, target-runtime acceptance |
| New or revised responsive type system | [`responsive-typography.md`](references/responsive-typography.md) | Semantic roles, fluid/container behavior, line measure, language and zoom acceptance |
| Edge-to-edge mobile, hybrid, or native layout | [`safe-area-layout.md`](references/safe-area-layout.md) | One owner per inset, orientation/keyboard checks, no hard-coded device table |
| Modal, drawer, toast, dropdown, popover, or tooltip selection | [`six-popup-types.md`](references/six-popup-types.md) | Task and modality choice, semantic role, focus/closing contract, recoverable feedback |
| Vague animation description or named motion effect | [`motion-description-vocabulary.md`](references/motion-description-vocabulary.md) | Trigger, subject, path, state outcome, reverse/cancel behavior, input modes |
| Component timing or motion-token audit | [`component-motion-tokens.md`](references/component-motion-tokens.md) | Semantic token mapping with interruption and reduced-motion checks |
| Completion burst, linked feedback, stacked fan, snap cards, inertial wheel, or circular reveal | [`six-app-interactions.md`](references/six-app-interactions.md) | Authoritative state, one motion owner, interruption/reversal behavior, target-surface acceptance |
| App or Mini Program component behavior | [`six-component-interactions.md`](references/six-component-interactions.md) | Authoritative state, keyboard/touch parity, settlement and announcement behavior |
| Rendering, 2D/3D, generated media, glass, scroll video, or advanced interaction choice | [`technology-selection.md`](references/technology-selection.md) | Chosen layer, important constraint, dependency/asset boundary, runtime proof |

Load only the references that answer a real decision. Reading every reference for a small change adds noise and weakens the route.

## Optional specialist integrations

The core does not require these tools or skills. When one is available and the task matches it, use it inside the direction already established by `frontend-experience`.

| Optional capability | Use it for | When it is unavailable |
| --- | --- | --- |
| `refero-design` | Bounded reference research for substantial web or product-screen design | Inspect user-supplied references, the current product, and relevant platform conventions. Do not claim live reference research. |
| `design-taste-frontend` | Landing pages, portfolios, and suitable visual redesigns | Continue with the design read, existing system, and supplied references. Do not invent a substitute aesthetic. |
| `emil-design-eng` or `apple-design` | Motion craft, gesture feel, springs, and spatial continuity | Use the state-transition contract and project/platform conventions in the core skill. |
| `oil-motion` | Scroll storytelling, asset planning, media compilation, and runtime mapping | Build the concept contract, storyboard, asset manifest, and deterministic frontend skeleton. Do not call an unconfigured generation provider. |
| `morphicons` | Compatible stroke-glyph transitions between semantic icon states | Use stable project icons and a simpler state transition; preserve accessible names and state semantics. |
| `3dviz-pro-max` | Grounded 3D explainers, spatial puzzles, and interactive scenes | Use the technology-selection questions directly and keep the deliverable within available 3D expertise and assets. |
| `img2threejs` | Reference-image-to-editable procedural Three.js reconstruction | Use an existing licensed model, a project asset pipeline, or stop at a documented asset plan if reconstruction is essential. |
| OpenPencil | Editable `.op` canvas artifacts and deliberate design-to-code handoff | Work directly in the established code or preserve Figma as the design source of truth. |

An unavailable optional tool is not permission to silently change the product goal, provider, asset source, media format, or production dependency.

## Worked examples

These examples are instructional specifications. They were not rendered by this repository and are not claims of pixel-identical output. Replace bracketed inputs with real project details and keep the project's own instructions authoritative.

### Example 1: responsive product page

#### Required inputs and assets

- an existing repository and its start/test/build commands;
- final product name, positioning, benefits, price or primary conversion action;
- logo and product imagery with usage rights;
- target desktop and mobile widths, representative languages, and browser support;
- the current design tokens or a clear brand palette and type direction; and
- the destination and success behavior of the primary CTA.

#### Copyable prompt

```text
Use $frontend-experience to design and implement a responsive product page in
[repository]. The primary visitor is [audience], and the primary task is
[conversion action]. Preserve [framework, routing, analytics, and existing
design-system constraints]. Use the supplied copy and assets; do not invent
product claims, testimonials, pricing, or logos.

First inspect the current page, shared components, tokens, fonts, assets, and
build commands. Give a short design read covering hierarchy, visual direction,
interaction language, required states, and desktop/mobile acceptance. Then
implement the smallest complete page in the existing stack.

Use references/responsive-typography.md for the type system,
references/safe-area-layout.md if the mobile page is edge-to-edge, and
references/technology-selection.md only if a rendering or motion choice is
unsettled. Keep text in the DOM. Prefer CSS or existing motion tools for simple
reveals. Do not add a production dependency unless the capability requires it
and the project permits it.

Verify the rendered page at [desktop size] and [mobile size], plus an
intermediate width. Exercise the CTA with keyboard and touch, 200% zoom,
long/localized copy, missing or slow imagery, visible focus, and
prefers-reduced-motion. Report the exact commands and observed runtime states.
```

#### Selected references

- [`responsive-typography.md`](references/responsive-typography.md) for semantic roles, fluid sizing, line measure, and language/zoom checks.
- [`safe-area-layout.md`](references/safe-area-layout.md) only when content can meet cutouts or system chrome.
- [`technology-selection.md`](references/technology-selection.md) only for an unsettled layer such as deterministic CSS motion versus media or WebGL.

#### Implementation sequence

1. Inventory existing layout, tokens, shared components, assets, and route behavior.
2. Define the content hierarchy: product identity, primary promise, proof, CTA, supporting details, and footer/legal content actually provided.
3. Establish type roles and line measure before decorative styling.
4. Build one complete desktop path with semantic landmarks and a real CTA destination.
5. Recompose for mobile based on priority; do not merely shrink the desktop layout.
6. Add only motion that clarifies entry, hierarchy, or state.
7. Exercise the runtime and correct overflow, focus, contrast, loading, and reduced-motion defects.

#### Important states

- initial load and font swap;
- image loading, missing image, and constrained network;
- CTA idle, focus, pressed, pending if applicable, success/navigation, and authoritative error;
- long copy and localization expansion;
- narrow, intermediate, and wide containers; and
- motion enabled and reduced motion.

#### Observable acceptance

- **Desktop:** hierarchy is clear without relying on viewport-specific crop tricks; main copy remains within a readable measure; assets do not shift the CTA after load.
- **Mobile:** content order follows user priority; no horizontal overflow; edge-to-edge content consumes each safe-area inset once; the CTA is reachable without hover.
- **Keyboard:** landmarks and focus order follow the visual task; every action has a visible focus state and activates with expected keyboard semantics.
- **Reduced motion:** the same content and final states remain available through shorter, simpler, or direct transitions; no blank media stage or hidden CTA appears.

### Example 2: stateful application screen

#### Required inputs and data

- the existing application shell, route, and permission model;
- representative rows, filters, metrics, and field semantics;
- the decisions users must make on the screen;
- authoritative API behavior for loading, empty, partial, error, and mutation results;
- desktop and mobile navigation constraints; and
- keyboard, touch, localization, and role requirements.

#### Copyable prompt

```text
Use $frontend-experience to redesign and implement the [operations/analytics]
screen in [repository]. The primary user is [role], and the screen must help
them decide or complete [task]. Preserve the current API contracts,
permissions, routing, framework, and shared design system.

Inspect the current screen, representative data, filters, table/list behavior,
navigation shell, mutation flow, and error handling. Use
references/dashboard-composition.md to establish decision-led hierarchy,
references/six-component-interactions.md for [named component behavior], and
references/component-motion-tokens.md only for transitions that already have a
clear semantic purpose.

Implement one complete path from entry through [filter/select/edit/submit] to
authoritative completion. Include loading, empty, partial-data, error, stale
response, pending, success, permission-denied, and mobile navigation behavior
that the real product can produce. Keep one source of truth for selection,
filters, and mutation status. Do not turn a UI collection into a backend or
authentication system.

Verify with representative data at [desktop size] and [mobile size]. Exercise
deep link and refresh, keyboard navigation, focus return, touch targets, rapid
filter changes, stale async responses, duplicate-submit prevention,
localization expansion, 200% zoom, and prefers-reduced-motion. Report observed
behavior separately from static screenshots or build success.
```

#### Selected references

- [`dashboard-composition.md`](references/dashboard-composition.md) for decision-led hierarchy, density, shell behavior, and representative-data verification.
- [`six-component-interactions.md`](references/six-component-interactions.md) for inline suggestions, expandable tags, scrubbers, text swaps, inline edit, or toolbar morph behavior.
- [`component-motion-tokens.md`](references/component-motion-tokens.md) for purpose-led timing instead of choosing a number by visual proximity.
- [`safe-area-layout.md`](references/safe-area-layout.md) if the mobile shell is edge-to-edge.

#### Implementation sequence

1. Map each data region and control to a user decision or action.
2. Remove or demote content that does not change a decision.
3. Define authoritative URL, local, and server state ownership for filters, selection, navigation, and mutations.
4. Build the primary data path with representative rows before tuning visual density.
5. Add empty, loading, partial, error, permission, and mutation states from real contracts.
6. Add stateful motion only after the source and destination states work without it.
7. Verify navigation, async ordering, accessibility, mobile composition, and recovery in the running app.

#### Important states

- cold loading, background refresh, partial data, empty result, and fatal error;
- default, filtered, selected, editing, pending mutation, success, and rejected mutation;
- stale results from rapid queries or filters;
- authorized, restricted, and expired-session behavior when the product supports them;
- expanded/collapsed navigation and wide-table handling; and
- interruption, cancellation, and reduced motion for every animated state change.

#### Observable acceptance

- **Desktop:** the first screen centers the primary decision; density comes from grouping and alignment; wide data remains navigable without hiding critical row context.
- **Mobile:** the primary task remains complete; navigation and filters have an explicit compact behavior; fixed regions respect keyboard and safe-area geometry.
- **Keyboard:** command/search, filters, table/list actions, menus, and inline editing have a coherent order, expected keys, visible focus, and correct focus return.
- **Reduced motion:** selection, pending, completion, filtering, and mode changes remain perceptible without large transforms or continuous motion.

### Example 3: substantial stateful motion interaction

#### Required inputs and constraints

- the existing component and motion stack;
- a precise source state and destination state;
- stable item identities and authoritative application state;
- supported pointer, touch, keyboard, and assistive paths;
- the allowed gesture threshold or product tolerance for accidental activation;
- target device performance constraints; and
- a reduced-motion design, not merely an animation-off switch.

#### Copyable prompt

```text
Use $frontend-experience to implement a stateful document-card interaction in
[repository]. A card opens into its detail surface from the invoking card,
returns to the same card on close, preserves stable identity across list/grid
changes, and enters multi-select through an interruptible long press with an
accessible non-gesture action.

Before editing, inspect every caller of the card, the route/state owner,
existing animation library, focus management, virtualized-list behavior, and
reduced-motion handling. Define the source and destination geometry, spatial
anchor, open/close path, list/grid measurement strategy, long-press threshold,
commit/cancel outcomes, drag or scroll conflicts, interruption behavior, and
focus transfer.

Use the stateful-motion and Advanced Interaction Techniques sections in
SKILL.md. Use references/motion-description-vocabulary.md to write the behavior
contract, references/technology-selection.md to choose the lightest capable
implementation, and references/component-motion-tokens.md only after each
transition has a semantic purpose. Reuse the existing motion stack; do not add
a dependency for an effect the platform, CSS/WAAPI, or the installed library
already supports.

Keep text and detailed content stable while the shell changes geometry. Keep
one state owner for open item, layout mode, selection mode, and selected IDs.
Support close, Escape/back, rapid reopen, mid-transition reversal, interrupted
long press, pointer leaving the target, scroll before threshold, resize or
orientation change, and item removal while open. Provide keyboard controls and
announced state changes.

Verify on real desktop and mobile targets with pointer, touch, and keyboard.
Inspect slow and rapid open/close, list/grid toggles, gesture commit/cancel,
scroll conflicts, focus transfer/return, reduced motion, clipping, layout shift,
and target-device frame behavior. Reject ghost duplicates, stretched text,
lost focus, an orphaned detail surface, or two systems writing the same
transform.
```

#### Selected references

- [`motion-description-vocabulary.md`](references/motion-description-vocabulary.md) for a precise trigger/path/state/reversal contract.
- [`technology-selection.md`](references/technology-selection.md) for choosing CSS/WAAPI, a platform transition, an existing motion library, or measured shared-layout logic.
- [`component-motion-tokens.md`](references/component-motion-tokens.md) for semantic timing and easing.
- `SKILL.md` sections **Preserve continuity in stateful motion** and **Advanced Interaction Techniques** for anchored reveal, FLIP/shared identity, REORDER, and interruptible long press.

#### Implementation sequence

1. Trace callers and state owners before changing the shared card.
2. Make open, close, list/grid, selection entry, selection exit, commit, and cancel correct without animation.
3. Measure the source and destination geometry from the rendered surface.
4. Add one coordinated transition owner for the shell; animate internal content separately only where needed.
5. Add gesture recognition with explicit threshold, scroll conflict, cancellation, and accessible parity.
6. Add interruption/reversal handling and lifecycle recovery for resize, navigation, or item removal.
7. Verify real frames and controls on desktop and mobile, then tune timing within the project's semantic tokens.

#### Important states

- card idle, focus, press, opening, open, closing, and returned;
- list, grid, and transition between them with stable identities;
- long-press waiting, cancelled, committed to selection mode, and selection-mode exit;
- rapid repeat, mid-transition reversal, route/back interruption, and resize/orientation change;
- item removed or filtered while open; and
- full motion and reduced motion.

#### Observable acceptance

- **Desktop:** open and close preserve the card's spatial origin; list/grid changes do not double-render content; pointer and keyboard paths reach the same states.
- **Mobile:** long press does not steal ordinary scroll before commitment; lifting, moving, scrolling, or crossing the threshold has an explicit outcome; system back closes the detail surface correctly.
- **Keyboard:** Enter/Space opens, Escape/back closes when appropriate, selection has a non-gesture command, and focus returns to the surviving source or a defined neighbor.
- **Reduced motion:** the same identity and focus relationships remain clear through a direct or short transition; state feedback, commit, cancel, pending, and selection are never removed.

## Verification report template

Use a short evidence record after implementation:

```text
Primary task:
Target runtime(s):
Implemented states:
Desktop observations:
Mobile observations:
Keyboard/touch observations:
Reduced-motion observations:
Automated checks run:
Unverified items and blockers:
```

Keep screenshots, build output, and tests as supporting evidence. State what was actually exercised and observed.

## Provenance and third-party material

This repository contains authored instructions and independent text summaries. It does not redistribute third-party screenshots, source videos, fonts, icons, components, models, or generated media.

Public projects and documentation mentioned in the skill remain governed by their own licenses and terms. A link or compatibility note is not permission to copy an upstream asset or add a dependency. Inspect the exact upstream version and license before adoption, preserve required notices, and verify the result in the target product.

## License

The files in this repository are licensed under the [MIT License](LICENSE). Third-party projects, trademarks, linked material, and assets that users may choose separately are not relicensed by this repository.
