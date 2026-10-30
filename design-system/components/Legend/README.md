# Legend

The OHLC row, the series rows (swatch, name, value at the crosshair) and the event-marker key, as text so you never have to read pixels.

**Consumer provides:** the OHLC values for the hovered or last bar, one `cs-legend__item` per drawn series with `color` set to its `chart-series-*` token (benchmarks get `cs-legend__swatch--dashed`), and the marker key for the event kinds present.

- Values use tabular figures (`numeric`). Missing bars show "—" and not 0.
- Benchmarks are dashed and named "vs SPY". The legend names the benchmark explicitly.
- Event markers always carry their letter (S, D, E), which fixes today's colour-only key.
