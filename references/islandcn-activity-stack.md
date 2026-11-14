# Persistent activity stacks and four-state status surfaces

Use this reference for a persistent top-of-screen activity surface such as an upload, timer, now-playing state, incoming call, delivery ETA, recording, build, live score, or two concurrent activities. It is not a general toast pattern and does not create an operating-system status surface.

This guide is an independent synthesis informed by the MIT-licensed [islandcn repository](https://github.com/opencoredev/islandcn), including its pinned [API](https://github.com/opencoredev/islandcn/blob/0011a41ea4882f3818caf35c98f3ee46b80c4a2c/skills/islandcn/references/api.md), [design guide](https://github.com/opencoredev/islandcn/blob/0011a41ea4882f3818caf35c98f3ee46b80c4a2c/skills/islandcn/references/design.md), [recipes](https://github.com/opencoredev/islandcn/blob/0011a41ea4882f3818caf35c98f3ee46b80c4a2c/skills/islandcn/references/recipes.md), [spring solver](https://github.com/opencoredev/islandcn/blob/0011a41ea4882f3818caf35c98f3ee46b80c4a2c/lib/island/spring.ts), and [motion parameters](https://github.com/opencoredev/islandcn/blob/0011a41ea4882f3818caf35c98f3ee46b80c4a2c/lib/island/motion.ts). Repository license and paths were checked on 2026-11-15. This repository does not redistribute islandcn code, registry items, icons, presets, or assets. Verify current framework, registry, and package requirements before adoption.

## Model activities, not notifications

An activity has stable identity, priority, optional group, authoritative data, a short accessible label, compact content, a minimal fallback, and expanded detail or controls. Start, update, alert, expand, collapse, and end mutate that activity; decorative animation never invents progress or success.

Use four visual states:

| State | Meaning | Content contract |
| --- | --- | --- |
| `idle` | no activity | no activity content |
| `compact` | one ongoing activity | recognizable leading mark plus one short trailing value |
| `minimal` | constrained or concurrent presentation | an even shorter representation of the compact pair |
| `expanded` | user asks for detail or an urgent event needs attention | context, value, detail, and relevant actions |

Always design compact and minimal forms. Provide expanded content whenever the activity has meaningful detail or controls.

## Optional islandcn adoption snapshot

The pinned [islandcn skill entrypoint](https://github.com/opencoredev/islandcn/blob/0011a41ea4882f3818caf35c98f3ee46b80c4a2c/skills/islandcn/SKILL.md) describes a React 19 and shadcn-registry route. If that exact route fits the existing project, add the core from:

```text
npx shadcn@latest add https://islandcn.dev/r/island-core.json
```

Treat the core and content items separately. The core supplies the activity engine and shell; add only the content components the selected activities require. In the pinned source, `island-content` installs `@hugeicons/core-free-icons` and `@hugeicons/react`, so adoption is not dependency-free even when the core registry item adds no package dependency. Review the generated registry diff and current package requirements before accepting it.

Mount exactly one `IslandProvider` and one `<Island placement="viewport" />` above components that can start activities. In Next.js App Router, keep that boundary in a client component. Do not mount another shell for each activity.

- Supply `compact` for every activity and a `minimal` representation with `MinimalPair` for constrained or split states.
- Use `withBubble` or `BubbleForm` when the compact trailing value cannot fit the secondary capsule.
- Use `glyphFrom` to adapt a compatible free icon when the included glyph set lacks the needed form; the pinned source's filled-form example passes `{ parts: "fill" }`.
- Inspect the generated component and icon licenses in the target project. This guide does not bundle the registry output or authorize package installation.

## Priority, grouping, and concurrency

When two unrelated activities run, the higher-priority one keeps the primary capsule; the other uses the secondary shape. If priorities match, stable start order resolves the presentation. A source-specific layout leaves only a small trailing area in the secondary capsule, so test the actual value rather than relying on truncation. Replace a wide time or label with a ring, glyph, meter, or one- to two-digit value when compacted.

In the examined source snapshot, the secondary capsule is `62.18` units wide and a `22 pt` glyph leaves roughly `20 pt` for trailing content; the primary trailing slot is designed around a maximum of about six characters or `72 pt`. These are implementation-specific fit budgets. Test the rendered type, localization, zoom, and target viewport rather than treating them as universal measurements.

Group activities only when they come from the same source and should take turns, such as orders from one shop or runs from one agent. Do not group unrelated tasks such as a timer and music merely to avoid designing concurrency.

Use an alert only for information the user needs now: an incoming call, failure, arrival, or meaningful score change. Routine progress is an update. A decision that must remain open, such as approval, should expand and remain actionable rather than auto-collapse like an alert.

## Map any event with three questions

1. **What is it?** Choose one recognizable glyph, avatar, crest, artwork, or progress form for the compact leading slot.
2. **What matters at a glance?** Choose one short, truthful value such as minutes, percent, score, gate, code, or heart rate.
3. **What is needed on inspection?** Put details and actions in the expanded state.

The same mapping supports timers, staged deliveries, builds, scores, sensor readings, prices, expiring codes, transcripts, approvals, and calls without treating presets as the product's information architecture.

## Spring and content-follow model

The source engine expresses springs with SwiftUI-style `response` and `dampingFraction`, solves them in closed form, and retargets from current value and velocity. This allows expansion to reverse into collapse without a jump. `blendDuration` mixes an in-flight trajectory into the new spring.

Its content-follow model lays each slot out at its resting geometry, then keeps its center at the same width and height ratios during container morphing. A source-specific scale relationship is:

```text
contentScale = (widthRatio * heightRatio) ^ (follow / 2)
```

Outgoing and incoming layers can overlap through blur, scale, and opacity to avoid an empty handoff. A sensor shell remains visually above content and does not move with it. The examined source updates SVG paths and content transforms outside React's per-frame render path; verify actual frame cost in the target product rather than treating that structure as performance proof.

The source expresses presence through contextual blur, scale, and an opacity power such as `opacity = presence ^ fade`; an alert applies the new content after a source-specific `0.12 s` delay so the container can begin expanding first. Both are choreography examples. They must remain interruptible and must not delay authoritative business state or assistive announcements.

The examined source records these contextual spring pairs as `response / dampingFraction` examples:

| Transition | Source value |
| --- | --- |
| appear | `0.483 / 0.62` |
| expand edge | `0.517 / 0.824` |
| expand height | `0.497 / 0.825` |
| collapse edge then retarget | `0.479 / 0.894`, then after `0.311 s`, `0.46 / 0.555` |
| collapse height | `0.453 / 0.928` |
| dismiss | `0.442 / 0.97` |
| resize | `0.5 / 0.82` |

These are source-specific fitted examples, not platform constants or brand defaults. Reusing the model does not require copying the numbers. Tune and verify on the target device, preserve current velocity on retarget, and document any departure.

The values and fit budgets above are source-reported calibration, not independently validated fidelity or performance results. The pinned repository notes that the original fitting recordings are not included, its comparison surface is incomplete, and a recording-reading test is skipped. Treat source names, takes, and fitted values as implementation evidence to reproduce and measure, not proof that another product matches the reference device.

## State and data ownership

- Give every activity a stable id; do not key state by visual index.
- Keep business status, progress, timer deadlines, and operation results in the product's authoritative state.
- Derive visual forms from that state. Do not use animation completion as proof that an operation succeeded.
- Update elapsed or remaining time from timestamps rather than incrementing display state each frame.
- End activities only when the underlying work ends or the user explicitly dismisses a dismissible result.
- Keep the activity surface from competing with the product's toast, banner, or system-notification regions.

## Accessibility and interaction

- Supply a concise activity label and announce meaningful updates through an appropriate live region; avoid announcing every frame or tick.
- Provide keyboard and touch routes for every expanded action.
- Long press can expand, but a visible click or keyboard route must also exist.
- External click or Escape may collapse detail when doing so does not discard a required decision.
- Preserve focus when compact and expanded content swaps; do not focus decorative status values.
- Reduced motion should keep status and controls understandable while reducing travel, morphing, blur, or spring overshoot.
- Use source names and visuals that do not imply official Apple integration or system-level behavior. Check trademarks and all icon or media licenses separately.

## Implementation sequence

1. Inventory existing banners, toasts, progress UI, and global shells; choose one owner and placement.
2. Define activity type, id, priority, group, authoritative fields, label, and lifecycle.
3. Design compact, minimal, and expanded forms with representative maximum-length values.
4. Implement start, update, alert, expand, collapse, end, and concurrent activity behavior before tuning motion.
5. Add interruptible container and content transitions that retarget from current state.
6. Add focus management, live announcements, pointer, touch, keyboard parity, and reduced motion.
7. Test one activity, two unrelated activities, a group handoff, a mid-transition reversal, a failure, and a required approval.

## Observable acceptance

- One activity reaches compact and expanded states without losing authoritative data.
- Two unrelated activities remain identifiable and actionable in the constrained layout.
- Grouped activities rotate without merging identity or state.
- A long trailing value has an intentional compact representation rather than accidental clipping.
- Expanding and immediately collapsing continues from current geometry and velocity.
- Routine updates do not trigger urgent alert behavior.
- An approval remains available until answered; its visual collapse does not resolve it.
- Keyboard, touch, pointer, focus, and live announcements agree with the visible activity.
- Reduced motion preserves the status and actions without the full morph.
- Unmounting or ending an activity removes timers, listeners, and animation work.
- Runtime inspection confirms layout, interruption, and frame behavior on target desktop and mobile widths; static documentation is not reported as that evidence.

## Copyable task prompt

```text
Design a persistent activity surface for [activities] in [product]. Reuse the
existing shell and notification system boundaries. Give each activity a stable
id, priority, optional group, authoritative data source, accessible label, and
idle/compact/minimal/expanded behavior. For each activity answer: what identifies
it, what one value matters at a glance, and what detail or actions are needed.

Implement routine updates separately from urgent alerts and persistent approvals.
Handle one activity, two unrelated activities, and same-source groups. Make the
container and content transitions interruptible and retarget them from current
value and velocity. Add keyboard, touch, focus, live-region, and reduced-motion
behavior. Test representative long values, mid-transition reversal, failure,
cleanup, desktop and narrow mobile widths, and actual frame behavior. Do not
claim OS-level integration or treat animation completion as operation success.
```
