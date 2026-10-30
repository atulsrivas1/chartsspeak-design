# ChartSettings

Personal chart settings: theme, candle colours, gridlines and event markers. It opens from the gear in `ChartToolbar`.

**Consumer provides:** a `Dialog` with `cs-setting` rows (name, hint, control). Changes apply live, and Done only closes the dialog.

- Candle colours default to Blue / orange (`chart-up`, `chart-down`). "Green / red" is opt-in (`chart-up-conventional`, `chart-down-conventional`) for people used to TradingView. Hollow-up/filled-down stays in both, so direction never depends on colour.
- Every setting here is personal view. Shared analysis (indicators, drawings) is never changed from this dialog.
- The engine receives the result as its theme object; see the Engine theme hand-off section.
