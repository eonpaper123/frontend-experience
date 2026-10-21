# Component motion: purpose before numbers

Use for modal, dropdown, panel, toast, badge, text/icon, and similar UI motion or a requested timing audit. Reference: [Transitions.dev](https://transitions.dev/) and its [official skill](https://github.com/Jakubantalik/transitions.dev/blob/main/skills/transitions-dev/SKILL.md), checked 2026-09-27. The skill lists 32 recipes while the README retains older 12/18 counts; counts and popularity are not selection criteria.

## Reusable rules

1. **Map by purpose, not numeric proximity.** Identify the element, trigger, entry/exit or update state, anchor, interruption behavior, and completion. Reuse the project's semantic motion tokens. Two equal durations can serve different purposes; an unmatched effect stays unchanged during an audit rather than being forced into the nearest token.
2. **Give entry and exit separate contracts.** A prompt, restrained close often serves dismissal better than replaying a celebratory entrance. The table below is an upstream starting point, not a platform standard. Tune against content, distance, frequency, input mode, and the existing motion system; do not slow urgent feedback to satisfy a preset.
3. **Scope distance and bounce to the effect.** There is no global 40px travel ceiling. A small decorative offset and a drawer traversing its real width are different jobs. Likewise, “bounce only on entry” is not universal: the upstream avatar recipe deliberately bounces on hover return. Preserve measured geometry, gesture settlement, reverse paths, and cancellation under the parent skill's continuity rules.
4. **Extract a recipe, not its demo.** Prefer CSS or WAAPI for matching simple behavior. Reuse or scope variables, classes, and keyframe names; a `t-*` class prefix does not isolate generic `:root` properties. Copy only needed rules after checking applicable usage terms; do not import demonstration dimensions, all catalog tokens, or an unneeded motion dependency. Enumerate animated properties instead of `transition: all`.
5. **Keep state semantics independent of animation.** Reduced motion must retain the intended final geometry and feedback, not merely hide the effect. Coordinate cleanup with real completion and superseding input; stale timers must not close a newly reopened surface. Keep modal focus, keyboard dismissal, input errors, busy/success state, and announcements authoritative. A reduced-motion CSS block alone does not prove accessibility.
6. **Review before applying.** For an audit, report file/line, semantic purpose, proposed token, and rationale without editing. Apply only within authorized change scope, then test rapid open/close/reopen, touch/focus paths, reduced motion, actual property ownership, and the rendered result. No matching token is a valid outcome.

## Upstream examples, not universal defaults

| Purpose | Upstream value | Interpretation |
| --- | --- | --- |
| Modal/dropdown open | 250ms | Entry reference; preserve anchor and focus behavior. |
| Modal/dropdown close | 150ms | Quicker dismissal reference, not a required global duration. |
| Panel open / close | 400ms / 350ms | Separate entry and exit tokens for that recipe. |
| Small text movement / text reveal | 4px / 12px | Local offsets, not limits on shared-element or page travel. |
| Avatar hover return | Strong overshooting easing | A documented counterexample to “no bounce on exit.” |

The upstream tokens use shared names such as `--duration-fast` plus per-recipe semantic variables. Preserve existing project vocabulary instead of globally renaming tokens to match this library. Several recipes also need JavaScript orchestration; portable CSS does not mean every behavior is JavaScript-free.

## Tool and reuse boundaries

The [README](https://github.com/Jakubantalik/transitions.dev/blob/main/README.md) advertises copy-ready snippets and generated skill references. This integration copies no upstream implementation and does not establish a blanket redistribution license; check the actual selected asset/code terms before reuse, including any Pro restrictions.

Do not run an installer merely to consult these rules. The upstream read-only `transitions review/refine` skill workflow is distinct from the **Refine live CLI**: `transitions-refine live` injects a script and starts a local relay; `--llm` can install/wire a persistent agent integration. Installing, injecting, starting services, or sending project data to an agent requires explicit task scope and inspection of the current tool. This learning update authorizes none of those actions.
