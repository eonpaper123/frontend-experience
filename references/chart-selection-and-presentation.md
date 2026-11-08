# Chart selection and presentation

Use this reference when selecting or reviewing charts in a client interface. Start with the reader's question and data relationship, not a wish for a more unusual shape. These twelve candidates are not exhaustive; ordinary lines, bars, and tables remain valid. For whole-page hierarchy, also use [dashboard composition](dashboard-composition.md).

## Choose from the data relationship

Establish the entities, measure and unit, period or cohort, aggregation, and denominator. Distinguish missing values from zero and decide whether negative values are meaningful. Give one short reason for the choice: “The reader needs to compare X; this encoding supports Y.”

| Question or relationship | Candidate | Required meaning and boundary |
| --- | --- | --- |
| Where does a quantity come from and go? | Sankey | Link width encodes compatible flow quantities. Name source, destination, and unit; account for losses or imbalance. Do not invent links or mix money with counts. Use bars or a table when dense crossings make comparison harder. |
| How does activity vary across calendar days? | Calendar heatmap | Aggregate by a consistent day and timezone; distinguish no observation from zero. Keep one color domain across comparable calendars. Use a line when precise temporal change matters more than recurring calendar patterns. |
| How do additive categories form a hierarchy? | Treemap | Area represents nonnegative additive parts and nesting represents a real hierarchy. Prefer sorted bars for exact comparison. Do not create unreadable tiny labels or silently group values as “other.” |
| How far is one bounded measure from a target? | Gauge | Show value, unit, range, and target; define overachievement rather than silently clamping it to 100%. A progress bar or bullet chart is often clearer for compact or repeated comparisons. |
| Where is a process now? | Stepper | Derive the step count and complete/current/pending/error states from the workflow. Equal spacing does not imply equal effort, time, or quantitative completion. |
| How does one cohort move through nested stages? | Funnel | Use a comparable cohort and window; state count and rate denominators. Do not force unrelated counts into a narrowing shape or infer the cause of loss from shape alone. |
| How do signed changes connect an opening and closing total? | Waterfall | Opening total plus signed changes must reconcile to the closing total. Anchor totals, label signs, and avoid counting subtotals twice. |
| What is the short trend beside a headline value? | Sparkline | Preserve time order, period, and a readable value and unit. Do not turn missing periods into zero. Share domains for magnitude comparison; disclose independent scaling when comparing shape only. |
| How did the same entity change between two conditions? | Dumbbell | Label both endpoints and compare like-for-like measures on one scale. Missing endpoints are not zero; the connector expresses difference, not causality. |
| How does actual compare with target? | Bullet | Show actual, target, unit, and a readable baseline. Add qualitative bands only when their thresholds have real definitions; above target is not always good for cost or defects. |
| How is one total composed? | Segmented or stacked bar | Parts must be mutually exclusive and complete with a common denominator. Label 100% normalization and show totals when total differences matter. Interior segments are weak for exact comparison. |
| What is the ranking and magnitude? | Horizontal ranking bars | Sort by the ranking metric and define tie behavior when needed. Leave room for full labels. Preserve natural time, stage, or ordinal order when that relationship matters more than rank. |

## Seven presentation decisions

1. **Palette expresses meaning.** Ordered lightness in one hue is a candidate for ordered magnitude, not a nominal-category rule. Name the data-hue roles, keep category meaning stable, and use diverging color around a meaningful reference. Labels, position, shape, or pattern must carry distinctions without color alone.
2. **Remove redundant gridlines, not reading aids.** Remove heavy decoration when direct labels replace it. Keep zero, useful ticks, target lines, and restrained grids when they support the task.
3. **Label directly when it reduces lookup.** Associate value, category or series, and unit. Label selected endpoints when every mark would collide. A legend remains legitimate for dense multi-series charts, and essential facts cannot exist only in hover.
4. **Order for the question.** Sort rankings by the selected metric; preserve chronology, workflow, and meaningful ordinal order. Keep order and color meaning stable across comparisons unless changed order is the point.
5. **Give attention a destination.** Annotate a real peak, exception, comparison, or target with evidence. One or two annotations are a useful starting point, not a cap that hides important alerts. Do not invent causal claims.
6. **Keep scales and definitions honest.** Length and area encodings need an honest zero reference. Ordinary bars start at zero and negative bars diverge from it; disclosure alone does not repair truncated bar lengths. Use a position-based dot or line chart when a narrow range is necessary. Label log scales and never place zero or negative values on them. Preserve units, windows, denominators, and normalization, and avoid dual axes that imply unsupported relationships.
7. **Interaction clarifies real data.** Make hover detail available to keyboard and touch where applicable. Show active filters and truthful loading, empty, and error states. Animate only when it helps track a real change and provide a meaningful reduced-motion state.

## Checkable acceptance

Use only checks relevant to the changed chart and inspect rendered output with a known data sample.

| Check | Observable evidence |
| --- | --- |
| Choice | State the reader's question, relationship, and why this encoding fits. |
| Data agreement | Compare totals, selected values, rates, labels, missing/zero meaning, cohort, aggregation, and denominator with the source sample. |
| Color roles | Count and name each data-hue role. Ordered color remains ordered and comparison charts reuse meaning. |
| Reading aids | Record which grids, baselines, targets, and labels remain and why. The reader can estimate values needed for the task. |
| Labels | Values, series/category, and units remain associated. Long labels and dense areas do not overlap or clip, and essential facts are available without hover. |
| Ordering | Rank order matches the measure; chronology and ordinal meaning remain intact. Ties do not imply false differences. |
| Scales | Domains, ticks, units, time windows, and denominators appear where needed. Zero, normalization, log, or independent scaling is valid and disclosed. |
| Small screens | At the supported small width and text zoom, labels, targets, and controls remain readable without silently changing the chart's meaning. |
| Color and text access | Non-color encodings carry necessary distinctions. Inspect applicable text and graphical-object contrast, and run a color-vision simulation as a diagnostic rather than treating it as the only accessibility check. Supply a concise accessible chart name and meaningful description; when detailed values matter, provide a structured, navigable data table instead of packing every value into one giant accessible label. |
| Interaction | Exercise keyboard, touch, filter changes, stale results, and reduced motion. Visible and accessible state remain synchronized. |

## Sources and rights boundary

The twelve candidate types were inspired by the public Xiaohongshu post [“Twelve chart types for AI interfaces”](https://xhslink.cn/o/1AmaPzMRiSK). Accessibility guidance follows [W3C WAI Complex Images](https://www.w3.org/WAI/tutorials/images/complex/). This reference is an independently written selection and acceptance guide, not redistributed media, component code, or proof of accessibility. It does not install or reproduce the source author's advertised private skill.
