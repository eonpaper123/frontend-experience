# Text motion vocabulary

Use these names to describe a text-animation intent and turn it into a testable brief. Choose motion only when it serves the content; important instructions and errors must remain immediately readable.

| Pattern | Useful for | Briefing boundary |
| --- | --- | --- |
| Typewriter | A short narrative or terminal-style reveal. | Reveal once, allow skipping, preserve complete text, and do not delay urgent content. |
| Text reveal | A title entering through a clip or mask. | Avoid distorting letterforms; recheck after font loading and wrapping. |
| Gradient text | A prominent word with a clear brand reason. | Check contrast across the actual background and keep ordinary copy static. |
| Split text | A short headline revealed by word, character, or line. | Preserve reading order, avoid layout shift, and keep text selectable. |
| Marquee | Nonessential logos or a continuing content strip. | Provide a persistent pause control, avoid duplicate announcements or tab stops, and keep the information available when motion stops. |
| Number ticker | A confirmed metric changing from a real old value to a real new value. | Keep the actual value available; do not animate invented data or announce every intermediate frame. |

For every pattern, retain one complete semantic text value for assistive technology and avoid duplicate visual fragments in the accessibility tree. Provide a meaningful reduced-motion state with complete, static content. Cancel or retarget animation when navigation, content changes, or a newer state supersedes it. Measure actual typography, localization, narrow viewports, zoom, and device performance. For continuous motion that must be pausable, follow [WCAG's Pause, Stop, Hide guidance](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html); for live announcements, see [MDN's `aria-live` reference](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live).
