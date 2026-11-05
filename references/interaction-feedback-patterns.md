# Interaction feedback patterns

Use this reference for game impact feedback, button press behavior, and task-workspace transitions. These are optional tools, not a checklist. The product's real state, platform semantics, and data contract remain authoritative.

No runtime dependency is required. Reuse the project's existing controls, motion tokens, form elements, and overlay primitives.

## Eight game-feedback techniques

| Technique | Game expression | Careful product-interface adaptation |
| --- | --- | --- |
| Hit-stop | A very brief pause at impact; the observed example used 4 frames | Reserve a brief local emphasis for a clear hit or success. Never pause the main thread, form input, reading, or a whole product surface. |
| Screen shake | Displacement rises with impact strength | If it fits at all, move only a small noncritical decorative container. Explain errors and warnings through text and state semantics. |
| White flash | The target flashes before disappearing; the observed example used 1 frame | Prefer a short border, tone, or selected-state change. Avoid full-screen flashes and repeated high-contrast flicker. |
| Debris | The observed example used 16 gravity-driven fragments | Use a few decorative particles only for a real destruction or removal event and only when they do not obstruct controls or content. |
| Squash and stretch | The object compresses at impact and elongates in motion | A pressable control may compress slightly, while its text, layout, hit target, and focus indicator remain stable. |
| Trail | Recent positions reveal the moving object's path | Use only for an object with a meaningful drag or travel path. Keep the trail away from targets, labels, and controls. |
| Rising combo cue | Consecutive hits raise the audio pitch | Prefer a visible count or restrained visual progression. Sound is optional, must respect mute and system volume, and cannot carry state alone. |
| Slow-motion finish | The final hit slows and pushes in | Limit this to a skippable, nonblocking celebration or result sequence. Do not delay the result, navigation, input, or return of control. |

The `4-frame`, `1-frame`, and `16-fragment` values describe one 60 fps demonstration; they are examples, not cross-device standards or general UI defaults. Advance time-based effects with actual elapsed time rather than assuming a fixed animation-callback interval.

### Translation boundaries

- Apply the authoritative state change before decorative feedback. Motion must not make pending work look successful, hide an error, or disguise performance problems.
- Choose intensity from the target surface, repetition rate, input method, and user sensitivity. Prefer weaker, shorter, local feedback that does not depend on color alone.
- Under reduced motion, remove or simplify displacement, shake, particles, and slow motion while preserving the same state, result, focus, and controls.
- A local emphasis in a product interface is not a game hit-stop. Never freeze a form, editor, thread, or page for an effect.
- Do not make sound the only status signal. Provide explicit controls when sound is a real product capability.
- The eight techniques are choices, not completion criteria. Static feedback can be the correct design.

## Button press and disabled feedback

1. **Compress slightly on press.** A scale of `0.96–0.98` over roughly `80–120 ms` is a starting range. Preserve layout, target size, and the visible focus ring.
2. **Settle from the current state.** Use a restrained spring or overshoot only when it fits the product. A new press, cancellation, blur, or gesture handed to scrolling must interrupt cleanly, restore the resting state, and avoid firing the action.
3. **Sink only a control with physical depth.** A physical button may move by `1–2 px` while its pre-drawn base weakens. Animate transform or opacity; do not change layout or recalculate box shadows frame by frame. Do not add depth to an established flat control.
4. **Explain why an action is unavailable.** Prefer persistent, readable text associated with the control. Native `disabled` controls cannot rely on focus or clicks to reveal a reason. If the product deliberately uses `aria-disabled="true"`, block activation through pointer, keyboard, and form-submission paths. An optional `2–4 px` local shake may supplement the explanation, but cannot replace it or imply that retrying will work.
5. **Acknowledge input without claiming success.** Press feedback may begin immediately; avoid the source's `0.4 s` delay before visible press feedback, and do not delay business activation for decoration. A perceptible response within about `100 ms` is a design target, not a measured result. Run the business action through the platform's normal click and keyboard activation, not on `pointerdown`. Pending, success, and failure come from the real operation, and animation must not create duplicate submissions.

Treat every number above as a tuning range. Test pointer, touch, keyboard, rapid re-press, cancellation, pending state, layout, focus, and disabled activation in the actual component. Under reduced motion, remove spring, sinking, and shake while preserving focus, text status, and non-color cues. For timing ownership, also see [component-motion-tokens.md](component-motion-tokens.md).

<a id="task-workspace-feedback"></a>
## Task workspace feedback

Use this recipe for Kanban/list switching, new-task dialogs, progressive task entry, attachment states, and comparable project-management or CRM workspaces. It is not a skeleton-loader recipe or permission to automate form entry.

1. **Change the view without changing the task.** Kanban and list views are projections of the same task records. Match by stable task ID, not array position, and preserve the current scope's filters, selection, and edit draft. The target should remain traceable through an appropriate scroll and focus context even when its pixel position changes. Apply shared-identity or FLIP motion only to elements that exist in both layouts; do not invent flight paths for virtualized rows. A view switch must not mutate task state or counts, reload the whole page, or leave both layouts visible.
2. **Return from the dialog to the action context.** Reuse the modal, focus, close, and draft-retention contracts in [six-popup-types.md](six-popup-types.md). An anchored expansion may use the real trigger position, but text must not stretch with its shell. Keep the backdrop behind the form and dependent pickers above it. Animation must not delay input or make closing the dialog look like a successful save.
3. **Let real input drive field feedback.** Names, descriptions, dates, priorities, and assignees come from user input, platform autofill, or an authorized business action. Do not copy a demonstration's example values, timed typing, forced focus order, or automatic field changes. Support paste, one-step fill, editing, clearing, and validation failure. Keep text labels for priorities and names for assignees instead of relying on color or an avatar alone.
4. **Separate file selection from upload completion.** Preserve a keyboard-operable file-browse path and add drag-and-drop only when the product supports it. A selected file may appear immediately, but distinguish local selection, real upload progress, completion, failure, removal, and replacement. Show progress only for an actual upload. Removing the last item restores the empty state without moving the browse or submit controls unexpectedly. Validate file limits at the product boundary, keep row actions reachable, and move focus deliberately after removal. Whether submit waits for attachments comes from the real API contract.
5. **Use color for a defined field.** Workflow status and priority are separate dimensions and should map to existing semantic tokens with persistent text or icon cues. Keep meanings consistent across cards, rows, and forms. A focus border is not proof of valid input. Update tasks, groups, and counts only after the authoritative success response; on failure, preserve correctable input and do not close the dialog as if creation succeeded.

### Task-workspace acceptance

On the target runtime, select a task and switch Kanban to list and back; verify its ID, filters, selection, groups, and counts. Open a task dialog, edit, cancel or close, and reopen it to confirm the defined draft and focus rules. Exercise attachment empty, selected, removed, uploading, completed, and failed states supported by the real product, then verify that submission changes the task only on the authoritative result.

Repeat the relevant path with keyboard, touch, a narrow screen and soft keyboard, rapid view changes, and reduced motion. The workspace must remain readable, operable, and data-consistent. These are acceptance requirements for a future implementation, not claims that this repository contains or has tested an application.

<a id="component-interaction-patterns"></a>
## Eight component interaction patterns

Use these recipes when a component lacks a clear action-to-result transition. Choose only the pattern that resolves the current task: steppers and progress for forms or orders; multi-select and long-press actions for lists or workspaces; accordions and flip cards for content; send feedback and filter chips for sharing or search. Reuse the project's components and source-search workflow first. The eight patterns are not a visual theme or a checklist to apply together.

Each recipe follows **action → immediate feedback → authoritative result**:

| Pattern | Behavior contract | Copyable implementation prompt |
| --- | --- | --- |
| Send or share button | Activate → show a small press and outgoing icon while the real operation is pending → show success, failure, or cancellation from the business result | Build a share button whose paper-plane icon leaves the control after activation. Show a truthful sending state, mark it shared only after authoritative success, and keep failure or cancellation actionable. |
| Long-press action menu | Meet the platform's long-press condition → lift the card and reveal actions → commit the selected action or restore the card on cancellation | Build a card action menu that appears after a valid long press, clearly shows the active destination, closes after selection, restores the card on cancellation, and offers an equivalent visible non-gesture entry. |
| Accordion | Activate a question heading → reveal its answer and move following content → keep the intended item open; in single-open mode, close the prior item | Build a single-open FAQ accordion with a semantic heading control, an answer that expands without overlap, keyboard operation, visible expanded state, and no focusable descendants left inside collapsed content. |
| Multi-select action bar | Select an item → reveal the shared action bar and count → keep the bar and every action bound to the same selection set; hide after the count reaches zero | Build a multi-select list with one authoritative selection set, synchronized item affordances and count, a safe-area-aware action bar, coherent exit, and deliberate focus return when the bar disappears. |
| Quantity stepper | Activate plus or minus → update the logical value immediately while the visible number rolls and the button settles → stop at the newest valid value and enforce the real bounds | Build an accessible quantity stepper whose buttons have names, whose current value is readable, and whose number motion never queues or decides the count. Use the product's bounds and step; zero is only an example lower bound. |
| Flip card | Activate → rotate around the vertical axis → expose the other side; activate again to return | Build a two-sided information card with keyboard activation and a reversible vertical-axis transition. Hide the mirrored back face visually and remove the inactive face from hit testing, focus, and assistive exposure. Inner links and buttons must not trigger the flip accidentally. |
| Filter chips | Change a condition → move the selected indicator and update results through a truthful loading transition → settle only when the selected condition and returned result agree | Build a filter control whose semantics match the real model, whose results handle loading, empty, error, and stale responses, and whose collection changes use stable IDs. Use `OUT → MOVE → IN` only when items actually leave, move, and enter; do not delay usable content for stagger. |
| Step progress | Complete the current step's validation and required save → change its marker to complete and fill the connection → highlight the next real step | Build a multi-step progress indicator whose completion comes from validation and required persistence, not animation time. Keep the description, current step, return path, failure state, and stored completion markers synchronized. |

### Component boundaries

- **Immediate feedback is not early success.** Decorative send motion does not own request state. Opening a platform share sheet does not prove that a recipient received content. Step completion comes from real validation and persistence. Do not add artificial waits.
- **Long press and multi-select are complete modes.** Resolve scrolling conflicts and cancellation, provide a non-gesture path, and use the project's menu focus and close behavior. In multi-select, item affordances, spacing, title or navigation, count, and action bar update from one selection source. Move focus before removing a bar that contains it.
- **Expansion, numbers, and flipping keep semantics.** Single-open accordion is a product choice, not a universal rule. A stepper updates from its latest logical value; animation does not serialize state. A flip card is a `rotateY` face transition, not the FLIP layout technique, and visual backface hiding does not by itself fix focus or pointer exposure.
- **Filter control and results own separate state.** Chips may represent single or multiple selection; do not convert them all into tabs. When an entire result set changes, wait for the selected query's usable response before replacing it. Associate each response with its condition so a stale response cannot overwrite a newer selection.
- **Choose the lightest implementation.** Existing semantic controls, CSS/SVG, WAAPI, or the project's motion runtime are usually sufficient. React, Tailwind, or Motion are optional stack choices. A normal flip card does not require Three.js. Morphicons may animate a matching glyph but does not own the container, collection, or business state.

### Component-pattern acceptance

1. The action and its intended result remain clear, including when several controls coordinate one mode.
2. Pointer, touch, and keyboard can complete the same task where supported. Long-press cancellation performs no action, and rapid input continues from the current state.
3. Pending, success, failure, and cancellation are truthful. Check selection returning to zero, stepper bounds, validation failure and back navigation, filter empty/error states, and stale-response rejection only where those paths exist.
4. Text, values, selected count, expanded state, and current step agree with data. Focus and reading order remain correct; color or motion is never the only result signal, and compact layouts keep overlays and action bars clear of necessary content.
5. Forward, reverse, interruption, and terminal states are defined before polishing motion. Reduced motion preserves the same information and controls through a direct or simpler state change, never a half-flipped card, vanished answer, or false completion marker.

## Sources and rights boundary

The game-feedback taxonomy was inspired by the public Xiaohongshu post [“Why does the version on the right feel better? Eight techniques”](https://xhslink.cn/o/xY6gnYFuYq) credited to Chengxuyuan Naiba. The task-workspace recipe was inspired by [“Day 827: Project management dashboard interaction motion”](https://www.xiaohongshu.com/discovery/item/6a8710ac000000000801192b) credited to Sheji Shi A-Can. The button notes credit MoChu AI Official as the source demonstrator.

The eight component patterns synthesize delivered descriptions rather than an independently viewed original video; they do not establish the source framework, animation library, duration, or business completion behavior. This reference is independently written and includes no source video, audio, images, or code. The demonstrations do not prove a production implementation, upload, save, timing, accessibility behavior, or framework choice.
