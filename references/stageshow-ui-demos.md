# Stageshow: authored product illustrations and cursor demos

Use [Stageshow](https://github.com/benjitaylor/skills/tree/main/stageshow) for illustrative product UI in a still, feature card, marketing or documentation hero, cursor walkthrough, or bento composition. It is not a production component system, replacement for a working application, or evidence of a real transaction. Keep the established project framework; its upstream kit uses React, while the composition approach can inform other stacks.

## Choose the output first

| Output | Starting point | Acceptance focus |
| --- | --- | --- |
| Still or feature card | A recognizable product fragment with one focal result. | Context, hierarchy, crop, and result at the actual display size. |
| Cursor demo | One meaningful action and its consequence. | Measured targets, press before result, causal movement, and a legible payoff. |
| System story | A consequence moving across related surfaces. | Explain the relationship without adding a simulated cursor unless it helps. |
| Bento grid | One leading tile with supporting details and varied content. | Judge the complete grid, establish one motion focus, and reflow legibly. |

Start from the closest upstream example when the kit fits, and replace its identity with the actual brief. Otherwise reuse the project's existing components. A copied demo title alone is not an adaptation.

## Compose a believable fragment

1. Define placement, still versus playback, focal object, action, payoff, and what can be omitted. Use legible words and values on the subject and result; decorative placeholder bars must not imply real production metrics or customer claims.
2. Frame at the final display size. Crop supporting content before labels, controls, or the payoff. Reposition or remove secondary objects for compact layouts instead of shrinking all text. Example card or viewport sizes from upstream are not universal breakpoints.
3. Treat bento as one composition: vary density, establish a lead tile, and avoid competing cursor loops. Reflow according to readability and the existing design system.
4. Write a short sequence of beats that ends in an understandable result. A single clear action is enough; example beat counts and loop durations are starting points only.

## Choreograph cause and result

- Measure named scene targets at each relevant size instead of guessing pointer coordinates. Keep carried objects and overlays anchored to what they refer to.
- Preserve object identity through label, size, and layout transitions. Use one animation owner per property and reuse the main skill's interruption and continuity rules.
- Let the result follow its depicted cause. Reset through a comprehensible undo, close, or concealed scene boundary. Hold the payoff long enough to read.
- Choose a settled poster that explains the result on its own. Reduced motion should show an intentional still or simplified composition, not a frozen transition. Keep meaningful information in text and do not present decorative fake controls as keyboard-operable controls.
- A staged cursor press is authored animation, not a DOM click. Do not connect illustrative scene scripts to payments, submissions, or other live operations.

## Inspect the rendered result

Check the opening and payoff at wide and compact sizes before reviewing the full animation. Then inspect the busiest intermediate frames, each depicted action, interruption, and one complete loop with its restart. Check both the isolated preview and the actual host page because host styles, clipping, and scaling can change the result. Review keyboard, touch, reduced motion, captions, and pause/stop behavior for ongoing automatic motion.

If using the upstream kit, read the relevant craft, framing, motion, rehearsal, verification, and API references. Its capture tooling can produce stills, state captures, and gates, but a clean gate does not prove visual quality, frame rate, keyboard behavior, or touch behavior. Inspect the resulting images and live playback. Record what was reused, changed, captured, and left unchecked in the project's existing acceptance notes.

## Reference-led demo and bento workflow

Apply these rules inside the composition and inspection requirements above:

1. **Start with one interaction.** Define one action, its visible consequence, a readable payoff, and an understandable reset before adding scenes. An illustrative inbox might show swipe, row departure and gap closure, count change, then undo. Preserve item identity on return. The scene remains an illustration, not proof that a production archive operation ran.
2. **Use authorized product evidence.** Begin with the product screenshots, code, components, and design tokens already available to the project. Map type, color, spacing, shell treatment, and real content structure before inventing a look. Remove sensitive information from inputs and exports. Access to local product code does not authorize sending it to an external tool or service.
3. **Give every bento tile a role.** Use the leading tile for the main feature story. Supporting tiles may show a close-up, a substantiated statistic, a relationship diagram, or an integration set. Share product tokens and spacing rhythm while varying density and visual weight. Equal tile sizes are valid when hierarchy remains clear. Never invent a metric to fill a tile; use real data or label it explicitly illustrative. Preserve the lead story in compact reflow and avoid competing automatic loops.

### Reference, plan, capture, and review

1. **Reference:** name the target slot and platform, shipping wide and compact sizes, reusable product UI and tokens, privacy boundary, and the one result viewers should understand.
2. **Plan:** choose the closest existing example or component. Write action → consequence → payoff → reset, choose the settled poster, and assign a role to each bento tile. Expand beyond one interaction only when the story needs it.
3. **Capture and review:** render in the real host. Inspect opening and payoff at both target sizes, then playback, busy intermediate frames, and the seam into the next loop. Fix hierarchy, crop, and text readability before fine motion. Report what was actually observed instead of treating a prompt, plan, generated file, or static gate as rendered acceptance.

## Installation and rights

See the [upstream repository](https://github.com/benjitaylor/skills/tree/main/stageshow), [skill instructions](https://github.com/benjitaylor/skills/blob/main/stageshow/SKILL.md), and [license](https://github.com/benjitaylor/skills/blob/main/stageshow/LICENSE). The upstream source is MIT; preserve its notice when copying code. Its [NOTICE](https://github.com/benjitaylor/skills/blob/main/stageshow/NOTICE.md) describes asset-specific boundaries; verify each brand mark, image, and other asset independently. MIT does not grant trademark rights or imply endorsement. This document summarizes a workflow and redistributes no kit code or media.

An illustrative feature card could show a user changing a generic editor button's accent color: select the button, open its color picker, choose a swatch, and hold on the resulting color. Keep the picker and button whole in compact framing, use no borrowed product logo, and show a still that communicates the result. The authored click changes scene state only. This is a planning example, not a claim that a demo has been rendered or accepted.
