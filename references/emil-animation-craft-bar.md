# Animation craft bar

Use this reference before adding interface motion, while reviewing an existing motion system, or when deciding whether an animation should exist at all. It sets a judgement and acceptance bar; exact curves and durations still belong to the user brief, project motion system, platform conventions, accessibility needs, and specific interaction contract.

This guide is an independent synthesis informed by the MIT-licensed [Emil Kowalski skills collection](https://github.com/emilkowalski/skills). The repository license and skill index were checked on 2026-11-15. No upstream skill files or examples are redistributed here.

## Ten standards

1. **Motion needs a job.** Use it for spatial continuity, state explanation, feedback, hierarchy, or avoiding an abrupt change. “It looks nice” is weak justification for a frequent action.
2. **Frequency controls intensity.** Remove motion from keyboard-triggered or extremely frequent actions; reduce it for repeated daily work; reserve expressive motion for rare or first-time moments.
3. **Reveal promptly.** Interface entrances usually need ease-out or a deliberate custom curve. Ease-in delays the part the user is waiting to see and needs a specific interaction reason.
4. **Keep routine UI brief.** Treat sub-300 ms as a review threshold for common feedback. Drawers, sheets, modals, and toasts can justify longer travel; other exceptions should state why.
5. **Honor the origin.** A popover, dropdown, or tooltip should emerge from its trigger. Avoid `scale(0)`; a small scale change such as `0.9-0.97` with opacity retains mass. A centered modal is a different spatial contract.
6. **Make reversal possible.** A frequent or gesture-driven transition must retarget from its current value and velocity rather than replay a one-way keyframe sequence.
7. **Prefer composited properties.** Use transform and opacity for continuous animation. Measure deliberate exceptions such as a clipped reveal or auto-height expansion; avoid animating layout properties as decoration.
8. **Implement reduced motion.** Reduce displacement, parallax, and continuous movement while preserving clear state feedback through opacity, color, or immediate layout. Gate hover-only motion behind hover and fine-pointer media queries.
9. **Let cause and response differ.** A deliberate hold or destructive confirmation may build more slowly; the system's acknowledgement should arrive quickly. Symmetric timings are not automatically correct.
10. **Keep a product character.** Motion should agree across components and with the product's tone. When its purpose or character is unclear, delete it.

These values are scoped review heuristics, not brand-independent laws. Gesture tracking, games, cinematic storytelling, and native platform transitions can require different timing or properties. Document the intended experience and test it on the real target.

## Patterns that require review

- `transition: all` instead of explicit property ownership;
- `scale(0)` entrances or fades with no spatial relationship;
- ease-in on a routine reveal;
- motion attached to keyboard shortcuts, command actions, or other high-frequency work;
- routine UI longer than 300 ms without an interaction reason;
- a trigger-owned overlay using a center origin;
- one-shot keyframes for a toast, toggle, or gesture that can reverse;
- animation of width, height, margin, padding, top, or left without a measured need;
- a parent CSS variable changing every frame to drive many descendant transforms;
- displacement with no reduced-motion result;
- hover animation on coarse or non-hover input;
- all elements entering simultaneously when hierarchy requires a short, bounded stagger.

## Delete-first remedy order

1. Delete motion that is frequent or purposeless.
2. Reduce duration, travel, scale change, or number of moving elements.
3. Replace a delayed or weak curve with a purpose-led curve.
4. Correct transform origin and apparent mass.
5. Make the transition interruptible and reversible.
6. Move continuous work to transform and opacity where the behavior permits it.
7. Separate cause timing from system-response timing.
8. Add bounded craft such as a short stagger, blur handoff, starting style, or spring only after the contract works.
9. Verify reduced motion, pointer gating, and consistency with adjacent components.

## Write the behavior contract first

For every transition, name:

- the trigger and supported input modes;
- the controlled subject and property owner;
- start, committed, cancelled, and reversed states;
- spatial origin and destination;
- what happens when the trigger repeats mid-transition;
- focus, reading order, and announcement behavior;
- reduced-motion behavior;
- the real target surface and frame-budget check.

Do not choose a library, curve, or keyframe until these answers are concrete.

## Optional specialist map

The upstream collection exposes narrow skills that can be consulted when available. They are optional source references, not required installations or substitutes for this repository's behavior contract:

- **Create one transition:** [animate](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/animate), then [choreograph](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/choreograph) for several coordinated elements, and [animation-performance](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/animation-performance) for frame-budget work.
- **Review an existing surface:** [review-animations](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/review-animations), then [remove-animations](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/remove-animations) or [improve-animations](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/improve-animations) according to the finding.
- **Translate vague language:** [animation-vocabulary](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/animation-vocabulary) names the mechanic before implementation.
- **Build gesture-driven motion:** [gestures](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/gestures) covers direct manipulation and interruption.
- **Work on mobile or native-feeling motion:** [mobile-native](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/mobile-native), [apple-design](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/apple-design), or [animate-expo](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/animate-expo) applies only when the target matches.
- **Record a proven project correction:** [learn-taste](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/learn-taste) can turn it into project guidance after evidence exists.
- **Choose a library or stress the UI:** [pick-ui-library](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/pick-ui-library) supports a bounded selection decision; [break-ui](https://github.com/emilkowalski/skills/tree/0f2e23b32bb1265e84cff8d3e75785fec953fb1b/skills/break-ui) probes long labels, empty sets, and large counts.

## Review output

Start with a compact table:

| Before | After | Why |
| --- | --- | --- |
| Exact current property, timing, or behavior | Exact proposed behavior | User-facing or technical reason |

Then report findings in impact order: interaction regressions; motion to delete or substantially reduce; performance; interruption and timing; origin and cohesion; accessibility. End with a clear result:

- **Block** when motion harms input, delays frequent work, starts from implausible geometry, animates avoidable layout work, cannot reverse where required, or omits an easy reduced-motion path.
- **Approve** when motion has a clear purpose, remains responsive, reverses correctly, stays within the target budget, and has a coherent reduced-motion state.

## Observable acceptance

- Keyboard, touch, pointer, and rapid repeat input reach the same authoritative state.
- Reversing during entry or exit continues from the visible state without a jump.
- Trigger-owned overlays use the trigger as their origin.
- Continuous animation stays within the target surface's frame budget.
- Reduced motion removes unnecessary displacement without hiding state change.
- Hover-only feedback does not become a required action on touch devices.
- The review distinguishes a project rule from a source-informed heuristic.
- No static code review is presented as rendered or runtime acceptance.

## Copyable review prompt

```text
Review the motion in [surface/component] against its actual interaction
contract. For each transition, identify trigger, subject, property owner,
origin, committed/cancelled/reversed states, repeat-input behavior, input
modes, focus/announcement behavior, and reduced-motion result.

Start with a Before / After / Why table using exact properties and values.
Prioritize motion that should be deleted, interaction regressions, performance,
interruptibility, timing, origin/cohesion, and accessibility. Test the rendered
surface with keyboard, touch, pointer, rapid reversal, and reduced motion.
Finish with Block or Approve and cite the observed evidence. Treat sub-300 ms,
ease-out entrances, and 0.9-0.97 scale starts as scoped review candidates,
not universal defaults.
```
