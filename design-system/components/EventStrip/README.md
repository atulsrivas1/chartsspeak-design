# EventStrip

"On this chart", the row under the chart, doubles as a map of time. A thin track sits on the chart's own time axis, with a tick at the date of each marker, drawing or event, and the visible window shaded. The chips below it list the same items, date first.

**Consumer provides:** each item's date (or "Range" for a whole-range item such as an indicator pair), author avatar, and label; the track's window (the zoomed range as a share of the loaded range); which item is current.

- **Choosing a chip moves the chart to that date** and makes its tick current (`data-active`, a heavier `ink` tick). This is personal view, like pan and zoom, so it never moves anyone else's chart.
- The track spans exactly the chart's plot area (from the panel edge to where the price axis begins), and each tick is placed by the engine from the item's date, so it sits under the bar it refers to. Never position ticks by hand.
- The shaded window appears **only when zoomed in**, showing where you are in the loaded range; dragging it pans. At full range there is no window (a full-width bar reads as a scrollbar). Off-screen items stay listed, with their tick outside the window.
- Ticks are neutral (`ink-muted`); the chip says who made the item. Colour is never the only signal.
- Under reduced motion the chart jumps instead of gliding.
