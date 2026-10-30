# LayoutBar

Chooses how many charts the workspace shows and what they share. It sits above the chart grid, in place of the single chart's title row actions.

**Consumer provides:** the current layout (1, 2 side by side, 2 stacked, 4), the sync toggles, and the Templates menu trigger.

- Layouts stop at four. Past four, slots fall below a readable chart on a 1440px screen, and the assistant can no longer say which chart you mean.
- **Which layout is shown is shared** (it's part of the workspace). **Sync is personal**: each person chooses what moves together on their own screen, and it never changes anyone else's view.
- Sync toggles: Crosshair, Interval and Date range are on by default; Symbol is off, because synced symbols make a four-chart layout show one stock four times.
- Changing the layout is undoable ("Undo change to 4 charts"). Removing a slot that holds someone else's indicators names them first.
- Each layout button has an accessible name; the icon is never the only label for screen readers.
