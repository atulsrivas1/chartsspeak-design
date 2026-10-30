# DrawingToolbar

A vertical strip down the left edge of the chart panel: pointer, line tools (trend, ray, horizontal), Fibonacci, rectangle, text note, measure, then snap, lock all and hide all.

**Consumer provides:** a `cs-drawbar` nav of `cs-railbtn` buttons with `aria-label`, `title` and `aria-pressed` (the active tool, and the on/off state of snap/lock/hide), using `cs-railbar__sep` between groups.

- Each tool draws with `DragHandle` anchors and nudge buttons. A drawing is shared and attributed, and appears in `ObjectList`.
- "Hide all" is personal view and says "Hidden in your view". It never deletes anything.
- Forecast and position tools are left out deliberately: ChartsSpeak gives no trade advice.
- Drawing tools are a demo-build feature today; ship tools one group at a time, lines first.
