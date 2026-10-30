# DataClassBadge

Says what the data is (class, adjustment basis, snapshot) in the fixed vocabulary, using neutral colour and a glyph.

**Consumer provides:** a `cs-badge` with a `cs-badge__glyph` and one of the fixed labels; `cs-badge--synthetic` (dashed edge) for synthetic data, `cs-badge--snapshot` for reopened evidence; the data run in `title` or a tooltip on the adjustment badge.

- Use the labels exactly: Synthetic, Stored daily, Stored 1-minute, Delayed; "Split-adjusted, not dividend-adjusted", "Raw (unadjusted)".
- Data class is not a state, so it is never green, amber or red. Synthetic data gets a dashed edge because it is the one most easily mistaken for real data.
- **One home per screen: the chart toolbar**, with the "through" date ("Stored daily · through 28 Oct"). Don't repeat it in the title, subtitle or footer. It also appears in the demo banner, every Evidence card and every export stamp, because those leave the chart.
- The badge is text with a glyph and no border, so it never looks like a button. Interval and chart type are controls, so they are buttons with a caret.
