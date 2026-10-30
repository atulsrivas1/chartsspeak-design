# ChartToolbar

The row above the canvas: the symbol button that opens `SymbolSearch`, interval and chart-type segments, the adjustment badge, Indicator and Compare, named Undo/Redo, and chart settings. A second row along the bottom of the chart panel holds range, go to date, reset view and the price scale.

**Consumer provides:** a `role="toolbar"` `cs-toolbar` containing `cs-symbtn`, `cs-seg` groups (buttons with `aria-pressed`), a `DataClassBadge`, compact `Button`s and `cs-toolbar__spacer`; the range/scale row is a second `cs-toolbar` placed under the canvas.

- Show only options that exist for the data. 1m and 5m appear only when intraday rows are stored. Bars, Line and Area show once the engine's chart-type switch ships. Types that need derived data (Heikin Ashi, Renko and the like) stay out until the no-calculation rule has an answer for them.
- Range buttons set the visible window and never fetch or calculate. "All" means all stored bars.
- Scale: Auto, Log, % (rebased to the first visible bar, the same rule as comparison) and Lock. Scale is personal view, so it is not part of undo.
- On desktop the row is 44px tall with 32px compact controls. On phone it scrolls sideways and its controls go back to 44px. The range/scale row folds into the settings sheet on phone.
