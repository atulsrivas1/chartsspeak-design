# AlertList

Alerts on **stored daily closes**. Each one shows its condition in words, its state with a glyph and a word, and when it was or will be checked.

**Consumer provides:** each alert's condition, state, and the check or trigger details.

- States: **Waiting** (◷, with the next check), **Triggered** (! `caution`, with the close that triggered it and the values compared), **Can't check** (⨯ `refusal`, with the reason), **Expired** (–).
- An alert never fires on stale data. If the symbol's data is behind, the alert says "Can't check" instead of staying silently Waiting.
- Triggered alerts appear in `ActivityFeed` under "Needs me" and as a `Toast` if the person is present. They never show an intraday price.
- Gated: the owner hasn't decided on live data. This design covers stored data only; real-time alerts would be a separate pattern with their own wording.
