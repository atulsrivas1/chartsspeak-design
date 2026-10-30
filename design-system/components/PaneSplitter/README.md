# PaneSplitter

Indicator panes under the price pane, each with a small header (name, value at the crosshair, settings, remove) and a draggable splitter between panes.

**Consumer provides:** `cs-pane` blocks (the engine draws inside them), each with a `cs-pane__head`, separated by a `cs-splitter` button with `role="separator"`, `aria-value*` (the share of height) and an `aria-label`. Arrow keys resize in 5% steps.

- Use at most two indicator panes, which is the product cap; `IndicatorPicker` explains it.
- Pane heights are personal view and are not part of undo.
- RSI's fixed 0–100 scale and its 30/70 reference lines are drawn by the engine. The header shows the value only.
