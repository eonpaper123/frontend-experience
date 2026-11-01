# Task-led dashboard patterns

Use these patterns as alternatives to dense data dashboards. Start with the user's decisions and the meaning of the data; do not add prominent metrics or charts without a real data contract. For deeper dashboard composition, see [dashboard-composition.md](dashboard-composition.md).

| Pattern | Composition | Useful when | Check |
| --- | --- | --- | --- |
| Asymmetric analytics | One primary measure, compact supporting metrics, a focused chart, and a separate schedule or queue when needed. | Comparing progress or capacity while keeping near-term work visible. | Keep units and time ranges explicit; on narrow screens reorder by task priority. |
| Editorial library | A clear introduction or featured item above a consistent image grid. | Browsing, comparing, and selecting visual work. | Preserve meaningful captions, image descriptions, keyboard selection, and useful crops. |
| Reading workspace | Current book or course leads the page, supported by progress and relevant actions. | Continuing a reading or learning task. | Changing the selected content updates its title and progress; date-range controls update the underlying data. |
| Operations overview | Attention items first, then service health, followed by delivery, cost, or security details. | Finding incidents and deciding what needs action. | Alerts and real status outrank decorative metrics; do not imply health while data is unknown. |

Treat light and dark themes as the same information architecture with appropriately adapted semantic colors. Do not delay urgent information for an entrance animation. Loading feedback should follow the real request state; reduced motion should retain a readable, stable view. For semantic chart and accessible data presentation, see [W3C's WAI tutorials](https://www.w3.org/WAI/tutorials/).

These are starting compositions, not templates to apply to every admin product. Validate filters, selection, permissions, empty and error states, long labels, keyboard use, and the actual compact viewport.
