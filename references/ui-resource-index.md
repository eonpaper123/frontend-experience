# UI resource index

Use this index to find one relevant component or interaction reference after checking the target project's own components. A public demo, preview, or source listing does not by itself grant copying, commercial-use, or redistribution rights.

| Resource | Useful for | Boundary |
| --- | --- | --- |
| [Stageshow](https://github.com/benjitaylor/skills/tree/main/stageshow) | Authored product illustrations, feature cards, cursor walkthroughs, and bento scenes. See [stageshow-ui-demos.md](stageshow-ui-demos.md). | Illustrative scenes are not production controls or proof of a live operation. Review the upstream license and asset notices before reuse. |
| [Bencho](https://bencho.dev/) | Browsing React interaction examples by behavior such as press, hover, drag, upload, or picker. | A live preview does not establish that source is available or reusable. Check the selected component, dependencies, and terms. |
| [SnapCN](https://snapcn.dev/) ([repository](https://github.com/shadcn-labs/snapcn), [MIT code license](https://github.com/shadcn-labs/snapcn/blob/main/LICENSE)) | React/Remotion video components such as text reveals, captions, device frames, and product scenes. | Intended for authored video, not a general web-control library. The code license does not cover every font, image, song, trademark, or rendering-service cost; review those separately. |
| [ReactDrops](https://reactdrops.dev/) | Selective React visual components. See [reactdrops-component-patterns.md](reactdrops-component-patterns.md). | Source terms differ from MIT; verify the selected version and distinguish product integration from redistribution as a library or template. |
| [React Bits](https://reactbits.dev/) ([GitHub](https://github.com/DavidHDev/react-bits)) | Specific React or Next.js source variants for a selected visual or motion behavior. See [GSAP, Lenis, and React Bits selection](gsap-lenis-react-bits.md). | The reviewed source uses MIT plus a Commons Clause condition: integration into an application is different from selling, sublicensing, or redistributing the components alone or as a competing pack. Review the selected commit, Pro/assets terms, framework variant, and any CLI dependency changes. |
| [Planes](https://useplanes.com/) | Discovering animated React or shadcn component candidates such as menus, cards, and inputs. | Confirm current source availability, framework version, pricing, and reuse rights before adopting. |

## Reuse checks

1. Search the project's own components first, then open only the resource category that matches the requested behavior and framework.
2. Inspect the exact source, dependencies, current license, platform fit, accessibility, and actual state behavior. Prefer reuse or the smallest adaptation; explain a concrete mismatch before writing a new component.
3. Keep interaction references separate from video or illustrative scenes. Verify the component in the real project, including keyboard, touch, focus, and reduced motion.
4. Do not install a dependency, migrate frameworks, or copy media merely because a directory or preview exists.

**Optional SnapCN adoption.** The official pinned [Quickstart](https://github.com/shadcn-labs/snapcn/blob/3f09f3a5fa0ee8ef7aea5e0680578471f9fdd339/README.md#quickstart) documents `npx shadcn@latest add @snapcn/text-reveal` for a selected registry item. Run it only after integration is authorized and only in an existing React/Remotion project with a working `components.json` and the required `@/` alias in both `tsconfig.json` and `remotion.config.ts`; the current README notes that Remotion's bundler does not read TypeScript path aliases by itself. The example import lands under `@/components/snap-cn/`, but the actual output follows the project's registry configuration. Inspect the selected item before execution and review the component, `package.json`, lockfile, aliases, and generated path afterward: the absence of a separate SnapCN runtime package does not mean the registry command cannot add dependencies or mutate configuration. This repository does not execute the command or bundle SnapCN code or media.

<a id="design-reference-resources"></a>
## Design references by page role

Use these optional entry points only after the overall direction is clear and one page role still needs a concrete reference. Select the source that answers the missing decision; do not turn the list into a required catalog tour. The links below are preserved candidate entry points from the installed source and were not live-rechecked in this sync. Before using one, confirm that the current page still exists, inspect what it actually provides, and review the selected asset or code's current terms.

| Missing reference | Candidate | Adaptation and rights boundary |
| --- | --- | --- |
| Scroll-led hero, cinematic composition, 3D or shader pacing | [Scrolltide](https://www.scrolltide.co/) ([terms](https://www.scrolltide.co/terms)) | Treat templates, prompts, source, and media as separate licensed items. Use a purchased or free item only within its current terms; do not copy it into this public skill or infer runtime acceptance from a showcase. Route implementation through the scroll-motion and technology-selection references. |
| Navigation grouping, mega menu, dropdown, sidebar, or breadcrumbs | [Navbar Gallery](https://www.navbar.gallery/) | Extract information architecture and entry grouping from a relevant example. A screenshot does not establish keyboard, touch, collapse, or source rights; route dashboard navigation through [dashboard menu patterns](dashboard-menu-patterns.md). |
| Footer hierarchy and closure | [Footer Design](https://www.footer.design/) | Adapt information grouping to the product's real legal, contact, and navigation content. Do not copy another brand or invent links to match a composition. |
| CTA copy, button/form hierarchy, newsletter, or pricing action context | [CTA Gallery](https://www.cta.gallery/) | Use the example to examine action priority and surrounding evidence, then build the control with the project's real state and [interaction feedback](interaction-feedback-patterns.md). A featured screenshot is not reusable product media or conversion evidence. |
| Translating a visual style into design-system roles | [Refero Styles](https://styles.refero.design/) and its [Linear example](https://styles.refero.design/style/90ce5883-bb24-4466-93f7-801cd617b0d1) | Treat exported tokens or CSS as reference material, not the named brand's official design standard. Map only the selected color, typography, and spacing roles into the existing stack; an export format is not a reason to migrate frameworks. |
| Hero composition and above-the-fold hierarchy | [Supahero](https://supahero.io/) | Study the relationship among headline, main visual, supporting proof, and primary action. It is a candidate gallery, not a default template source or permission to copy a featured brand. |
| Consistent 3D icons for onboarding, empty states, or decorative explanation | [3dicons](https://3dicons.co/) and the [V1 collection](https://3dicons.co/collection/b68cf8-v1) | Verify the selected collection's current license and whether the delivered item is a rendered image or model. A collection marked CC0 does not make paid collections or editing services CC0, and a downloadable model is not automatically suitable for real-time rendering. Functional icons still need a readable silhouette and accessible label. |

When a source is selected, record the exact page or asset, the single structure or behavior being borrowed, how it maps to project tokens and content, and what rights or runtime behavior remain unverified. A reference screenshot does not replace observing the source interaction or testing the resulting project at its target sizes and input modes.

<a id="contract-led-delivery"></a>
## Contract-led delivery candidate: Fable Design

[Fable Design](https://github.com/ustoppble/fable-design) is a public workflow candidate for turning a design brief into coordinated sections. At the reviewed commit `dc6a9ba14bb97367dffccbfb98b07b36a52cde96`, the repository exposed no license file through GitHub. Public visibility is not permission to copy its templates or implementation; use only the independently synthesized delivery lessons below unless rights are established.

- Define the shared shell, tokens, content/data shape, motion ownership, and integration boundaries before parallel section work. Each contributor should know which surface it owns and which shared contract it must preserve.
- Translate declarations into observable acceptance. The existence of an import, screenshot, selector, or DOM marker proves only that narrow fact; it does not prove the visual result, interaction, responsive behavior, or main product task on the target runtime.
- When verification fails, repair the failing layer: the shared interface, the local section, the actual runtime behavior, or the check itself. Do not add ceremony or unrelated auditing to compensate for an incorrect boundary.

Do not inherit a fixed number of agents or sections, a prescribed model, virtual scrolling, a preloader, 3D, shaders, palette ratios, typography ratios, frame-rate claims, or DOM-marker checks from a reference workflow. Select only what the real product requires and verify it on its actual surface.
