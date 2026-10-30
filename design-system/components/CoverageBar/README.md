# CoverageBar

How much of the chart's range is actually stored, with gaps hatched in `caution` and the unstored tail left empty.

**Consumer provides:** a `cs-coverage` with an `aria-label` that states every stored and missing range in words, a title row with a `Partial coverage` badge when there are gaps, the `cs-coverage__bar` segments, and an axis line naming the gap and the "stored through" date.

- Used in the Data tab, the symbol search details and the first-run step. On the canvas the same gap is shown with `cs-gapband` over the missing dates.
- Gaps are never interpolated or bridged on the chart. Lines break at the gap.
