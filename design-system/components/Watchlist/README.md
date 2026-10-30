# Watchlist

The symbols someone keeps an eye on, as a rail tab. Every value is the last **stored** daily close, with the date it's stored through. Nothing here is real-time, and the panel says so.

**Consumer provides:** each symbol with name, last stored close, change on the previous stored close, stored-through date, and whether it's stale or not stored.

- The change uses a ▲ or ▼ glyph in the candle colour; the number itself stays in `ink`, because `chart-down` is under 4.5:1 for text on light surfaces.
- Stale (stored through an earlier date than the rest) shows "! through 3 Oct" in `caution`. Not stored shows only "Not stored": no number, no dash, no estimate.
- Selecting a row opens that symbol in the active chart slot. The current one is marked with `aria-current`.
- The watchlist is personal by default; a workspace can have a shared one, shown with its author like any shared object.
- No sparklines: a tiny chart beside a stored value reads as live.
