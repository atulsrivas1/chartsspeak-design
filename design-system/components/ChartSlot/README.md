# ChartSlot

One chart inside a multi-chart layout. Every slot keeps the full honesty vocabulary of the single chart: data class, stored-through date, and its own state (Updating, Not current, Not stored).

**Consumer provides:** symbol, interval, data class, stored-through date, active state, and either the engine canvas or an `EmptyState`.

- **One slot is active**: it gets the accent outline and the word "Active" in its head, so it isn't shown by colour alone. Keyboard shortcuts, the indicator picker and the assistant act on the active slot. Click or Tab into a slot to make it active.
- Slots fail on their own. One slot reconnecting or not stored never veils the others.
- A slot whose symbol isn't stored shows `EmptyState` with the utility command, never a placeholder chart.
- **Phone:** layouts collapse to one chart at a time with a slot switcher (symbol tabs) above the chart. The layout itself is unchanged, so it comes back on desktop.
- **Tablet:** 2 side by side stays; 4 becomes 2 stacked with a switcher for the other pair.
