# IndicatorPicker

The Add indicator popover: stored presets grouped as on-price overlays or own-pane indicators, with the pane cap and the not-stored refusals shown in place.

**Consumer provides:** the `cs-popover` + `cs-list` pattern (as `SymbolSearch`) with `aria-multiselectable`; each row's sub-line states where it draws and its coverage; an "On chart" meta on selected rows.

- The pane cap is named in the group header ("2 of 2 in use"), and blocked rows say what to remove. A third pane is never silently ignored.
- A custom period typed into search becomes a "Not stored" row with the utility instruction. Nothing is computed.
- Indicator style (colour, width) is not editable yet. Series colours come from `chart-series-*` in order.
