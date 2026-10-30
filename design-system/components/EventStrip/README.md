# EventStrip

"On this chart", the row under the chart, doubles as a map of time. A thin track sits on the chart's own time axis, with a tick at the date of each marker, drawing or event, and the visible window shaded. The chips below it list the same items, date first.

**Consumer provides:** each item's date (or "Range" for a whole-range item such as an indicator pair), author avatar, and label; the track's window (the zoomed range as a share of the loaded range); which item is current.

- **Choosing a chip moves the chart to that date** and makes its tick current (`data-active`, a heavier `ink` tick). This is personal view, like pan and zoom, so it never moves anyone else's chart.
- The track aligns with the chart's plot area (it stops where the price axis begins), so a tick sits under the bar it refers to.
- When zoomed in, the shaded window shows where you are in the loaded range; dragging it pans. Off-screen items stay listed, with their tick outside the window.
- Ticks are neutral (`ink-muted`); the chip says who made the item. Colour is never the only signal.
- Under reduced motion the chart jumps instead of gliding.
