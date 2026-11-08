# Motion curves by scenario

Use this map after the state transition is defined and the project needs an easing candidate for entry, exit, in-place movement, or a constant loop. It does not replace gesture physics, springs, motion paths, or existing semantic motion tokens.

## Define purpose before choosing a curve

Name the element, trigger, start and end states, whether it enters, exits, or moves within the surface, and how it reverses or interrupts. The CSS equivalences below follow [W3C CSS Easing Functions](https://www.w3.org/TR/css-easing-1/#cubic-bezier-easing-functions). They are candidates, not Apple curves, brand rules, or universal defaults.

| Scenario | Candidate | Why consider it |
| --- | --- | --- |
| Rotation or a constant-speed loop | `linear`, equivalent over 0–1 to `cubic-bezier(0, 0, 1, 1)` | Constant progress avoids a visible acceleration seam on every cycle. The first and last frame and spatial speed still need inspection. |
| Accelerating departure | `ease-in` = `cubic-bezier(0.42, 0, 1, 1)` | A slower start followed by acceleration can make a surface read as moving away. It is not the default for every close action. |
| Entry | `ease-out` = `cubic-bezier(0, 0, 0.58, 1)` | Establishes visible response quickly and slows near the destination. |
| In-place relocation, expansion, or coordinated page change | `ease-in-out` = `cubic-bezier(0.42, 0, 0.58, 1)` | When both endpoints stay visible, a slow-fast-slow curve can keep the path trackable. Frequent feedback may feel delayed by the slow start. |
| Product motion identity | A project-selected `cubic-bezier(x1, y1, x2, y2)` | Tune the beginning, acceleration, and settlement for a named purpose, then reuse it through the existing token system. |

The graph's horizontal axis is input progress and its vertical axis is output progress; slope indicates rate of progress. It is not the object's screen path or a velocity-over-time graph. `x1` and `x2` must remain in `[0,1]`; `y` may extend outside that range. Overshoot must make sense for the animated property. Constant progress does not guarantee constant spatial speed on a nonuniform path, and a cubic Bézier is not a physical spring.

## Reconcile competing advice

- Do not label every ease-out exit as wrong. The [practical motion checks](component-motion-tokens.md#emil-practical-checks) retain an alternative recommendation of ease-out for quick enter and exit feedback. Choose from the product contract, visible path, frequency, and observed feel.
- Ease-in on entry can hide the start of feedback. Try ease-out first when response must be immediate; keep ease-in only for a deliberate acceleration.
- Linear can look mechanical, and that can be the correct purpose. Do not add ease-in-out to a constant spinner or direct pointer tracking. Inertia and release settlement belong to the gesture model.
- A curve cannot repair wrong state or geometry. Do not use easing to hide stretched text, stale results, layout jumps, delayed actions, or an incorrect close contract.
- Standard CSS keywords are not aliases for every custom curve with a similar name. Verify spring, bounce, elastic, and stepped behavior in the selected runtime rather than approximating all of them with one Bézier.

## Minimal WAAPI mapping example

This example hands selected candidates to the project's existing animation owner. The caller supplies duration; this reference does not add a parallel controller.

```js
const easingByRole = {
  constant: 'linear',
  enter: 'cubic-bezier(0, 0, 0.58, 1)',
  leaveAccelerating: 'cubic-bezier(0.42, 0, 1, 1)',
  relocate: 'cubic-bezier(0.42, 0, 0.58, 1)',
};

function motionOptions(role, durationMs, reducedMotion) {
  return {
    duration: reducedMotion ? 0 : durationMs,
    easing: easingByRole[role],
  };
}
```

`role` is an internal, already selected purpose. Existing project tokens take precedence. The caller still cancels prior work, continues from the current visual state, commits the final state, and manages focus. Zero duration is an explicit direct transition; it does not update DOM, focus, or announcements by itself.

## Target-runtime acceptance

Compare candidate curves on the same element, path, and duration. Check whether feedback begins promptly, entry settles cleanly, exit feels delayed, and in-place movement remains trackable. Exercise reverse direction, rapid reopen, interruption, and the explicit terminal state. For a constant loop, inspect the seam. Under reduced motion, preserve the same information and operation result. Keep the existing keyboard, touch, focus, and state-result contracts.

## Evidence boundary

The four standard CSS curves were checked against W3C CSS Easing Functions. Scenario mappings are design candidates synthesized from demonstration material; no duration, spring, damping, brand curve, live animation, or target-device performance is established by this file.
