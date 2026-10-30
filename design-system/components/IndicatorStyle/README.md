# IndicatorStyle

The style editor for one indicator: colour, picked only from the chart palette (`chart-series-1…5`), and line width.

**Consumer provides:** a `cs-popover` with a live `cs-linepreview`, a `cs-swatches` radiogroup (swatches already used on this chart are `aria-disabled`, with the owner named in their label), a width `cs-seg`, and Done.

- There is no free colour picker. The palette is what keeps lines distinguishable and readable in both themes; an arbitrary colour could fail contrast or match the candles.
- Style is personal view. The shared item keeps its colour for everyone else, and the legend shows your colour.
- Benchmarks stay dashed whatever colour is chosen.
