# DataClassBadge

Says what the data is (class, adjustment basis, snapshot) in the fixed vocabulary, using neutral colour and a glyph.

**Consumer provides:** a `cs-badge` with a `cs-badge__glyph` and one of the fixed labels; `cs-badge--synthetic` (dashed edge) for synthetic data, `cs-badge--snapshot` for reopened evidence; the data run in `title` or a tooltip on the adjustment badge.

- Use the labels exactly: Synthetic, Stored daily, Stored 1-minute, Delayed; "Split-adjusted, not dividend-adjusted", "Raw (unadjusted)".
- Data class is not a state, so it is never green, amber or red. Synthetic data gets a dashed edge because it is the one most easily mistaken for real data.
- Show it in the chart toolbar, the demo banner and every Evidence card. Do not show it in the top bar.
