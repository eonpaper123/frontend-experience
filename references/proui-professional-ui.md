# ProUI for Professional Workstation Interfaces

Use this reference when the product is a high-density professional workstation: a multi-panel editor, DAW, video or image tool, game engine, PCB workspace, or mission planner. [ProUI](https://pro-ui.dev/) is a commercial editable-source option whose useful reference is the workstation interaction grammar and composed workspaces. It is not a default component library for ordinary sites.

## Current offer and platform boundary

The official site checked on 2026-10-30 advertises 77 React components, 107 icons, and six application templates. Counts can differ by platform or catalog revision, so inspect the current target-platform registry before selecting a package. The React guide currently requires React 19, TypeScript, Tailwind CSS 4, and shadcn. SwiftUI is provided as a local source kit. The GPUI guide currently targets GPUI 0.2.2 and Rust 1.92. Recheck the live guide when implementing.

| Template | Demonstrated workspace |
| --- | --- |
| Forma | Image editing |
| Cadence | Digital audio workstation |
| Splice | Video editing |
| Foundry | Game engine |
| Trace | PCB design |
| Apogee | Orbital mission planning |

Each template is presented as a web application with a thin Electron project. Treat its processing, simulation, and domain operations as demonstrations. Inspect the source and replace simplified behavior before relying on it as a production engine.

## Decide whether it fits

- For a dense workstation, inspect the matching ProUI template and component contracts before building panels and precision controls from scratch.
- For a marketing page, simple dashboard, or lightweight form, start with the project's existing design system or an appropriate free primitive set. A professional-tool library does not create professional product behavior by itself.
- If ProUI's visual system conflicts with the product, reuse only the needed interaction contract or licensed component while preserving brand, accessibility, keyboard behavior, and application architecture.
- Compare time saved in precision controls and workspace composition against license cost, target-platform maturity, integration work, and long-term ownership of copied source.

## Interaction contracts worth preserving

Confirm the selected component's actual implementation before relying on these behaviors.

- **Controls:** Button, Slider, Menu, and Knob. Check pressed-state continuity across frames. Sliders should support value entry, drag, keyboard, and reset when those paths belong to the task; knobs should track the gesture and settle precisely. Keep value changes reversible.
- **Bars:** Action Bar, Sub Bar, Toolbar, and Scopebar. Reserve enough trigger width for the longest label, and keep selection and action state legible in dense groups.
- **Panels:** Titlebar, Inspector, Disclosure Group, and Statusbar. A collapsed disclosure can retain a concise value summary. Keep status information quiet but findable.
- **Forms and inputs:** Select by the task, then inspect keyboard, focus, value entry, reset, validation, and disabled behavior rather than copying surface styling alone.
- **Electron:** Titlebar drag regions must exclude interactive descendants using `pro-no-drag`. Native window buttons and OS actions remain owned by the host bridge.

Keep keyboard access, visible focus, correct accessible names and values, and state restoration when adapting any pattern. A live demo is not an accessibility or production-readiness audit.

## React installation and agent discovery

Read the official [agent catalog](https://pro-ui.dev/llms.txt) and [React setup guide](https://pro-ui.dev/guide.md) before an authorized integration. The catalog currently lists `pro-button`, `pro-titlebar`, and `pro-theme` as free entries without a registry token. A documented source-install command is:

```sh
npx shadcn@latest add @proui/pro-button
```

The guide also supports a direct registry URL:

```sh
npx shadcn@latest add https://pro-ui.dev/r/pro-button.json
```

Use the project's package manager and shadcn aliases. Paid registry entries and application templates require an authorized license token. Do not add a bearer token to registry configuration unless it is actually available; the official guide warns that an authorization header can make free installs require the token too. Inspect the chosen registry entry's dependencies and shared styles before installation, and do not install anything for a recommendation-only task.

Official examples include [image editor](https://pro-ui.dev/examples/image-editor), [DAW](https://pro-ui.dev/examples/daw), [video editor](https://pro-ui.dev/examples/video-editor), [game engine](https://pro-ui.dev/examples/game-engine), [PCB designer](https://pro-ui.dev/examples/pcb-designer), and [mission planner](https://pro-ui.dev/examples/orbital). Treat them as product demonstrations, not source rights or independent reviews.

## Price and license boundary

As checked on 2026-10-30, the official pricing page lists US$99 once for one platform and US$149 once for all three. The vendor states lifetime updates, unlimited projects and seats, commercial use, and the right to keep and modify the source. These are vendor claims; recheck the live offer and applicable purchase terms before spending money or delivering source.

The homepage FAQ permits client work and products for sale, while prohibiting redistribution of ProUI itself as a competing component library or template kit. A finished client product is different from resale of reusable development assets. For a case the published terms do not clearly settle, such as transfer of a standalone source kit, check the actual purchase and license terms before distribution. Free registry entries still retain their stated license and notice requirements, and SwiftUI and GPUI kits have platform-specific access conditions.

Do not buy a full workstation library to make an ordinary page appear professional, copy a paid template from its preview, infer accessibility or performance from polish, or strip keyboard input and recoverable state while copying the look. This reference contains independently written selection guidance. It includes no ProUI component source, paid template, vendor asset, purchase, installation, build, or rendered verification.
