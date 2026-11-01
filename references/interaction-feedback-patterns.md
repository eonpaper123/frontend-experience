# Interaction feedback patterns

Use these ideas for game hit feedback and small button-state transitions. They are optional tools, not a checklist. The product's real state and interaction semantics remain authoritative.

## Game feedback, adapted carefully

Game effects such as brief hit pauses, screen shake, flashes, particles, squash-and-stretch, trails, rising combo cues, and slow-motion finishes can clarify a game event. Use them only when they fit the action. In a product interface, prefer a brief local emphasis; do not freeze a form, editor, page, or thread. Never use motion, sound, or color as the only explanation of a result. Avoid full-screen flashes and repeated high-contrast flicker.

State changes must happen before celebratory feedback. Respect reduced-motion settings by removing or simplifying movement while preserving the same status, result, focus, and controls. Sound should be optional, user-controlled, and never the only feedback. Values shown in game demonstrations are examples, not cross-device timing standards.

## Button press behavior

- A small press scale, such as `0.96–0.98` for roughly `80–120 ms`, can be a starting point. Preserve the button's layout, target size, and visible focus ring.
- Use a restrained release spring only when it fits the product. New presses, cancellation, blur, or a gesture handed to scrolling should settle from the current state without firing the action.
- A button with a clear physical base may move by a small amount while its base appears compressed. Keep animation on transform or opacity; avoid changing layout or recalculating shadows frame by frame.
- Explain disabled actions with persistent nearby text when possible. Native disabled controls cannot be relied on to reveal a reason through focus or clicks. If a product intentionally uses `aria-disabled`, block activation through pointer, keyboard, and form submission paths.
- Press feedback may begin immediately, but submit through the platform's normal click or keyboard semantics. Pending, success, and failure follow the real operation; animation must not cause duplicate submission.

The numeric values above are tuning examples, not measured universal standards. Check pointer, touch, keyboard, rapid re-press, cancellation, pending state, focus, and reduced motion in the actual component. For stateful interaction timing, also see [component-motion-tokens.md](component-motion-tokens.md).
