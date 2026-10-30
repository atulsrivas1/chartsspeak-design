# LocalCrosshair

Two neutral lines that show where the pointer is, drawn in the browser from engine geometry before the engine's own crosshair frame arrives (R1 A-G2). They never show a value. Source of truth: `ARCH-geometry-zoom-px.md` section 5; board 44 in the screens canvas.

**Consumer provides:** a `cs-xhair` layer over the plot rect (`right: 64px` clears the price axis), with `cs-xhair__v` at the snapped `bar_x` and `cs-xhair__h` at the pointer's y. In the app this is the SDK's `createCrosshairOverlay`; this component only fixes how it looks.

- **Look:** 1px, `chart-crosshair`, dash 3 on 3 off: identical to the engine crosshair, so when the engine's point frame paints the two coincide and nothing jumps.
- **Never on the overlay:** price, time, bar value, axis tag, tooltip, label, dot, glow or "live" styling. No animation and no fade.
- **Values** appear only in the engine read-out (the OHLC row), which always carries its own date.
- **Shown only when all six rules hold**, removed at once otherwise: (1) geometry belongs to the painted, verified frame; (2) the viewer is ready; (3) the painted frame is current (not stale, superseded, a Snapshot or Replay); (4) no pan or zoom gesture pending and no pan bridge active; (5) the pointer is inside the plot rect, the window is focused and the tab visible; (6) no resize in flight. In each failed case the person sees the state the system already shows (veil, Updating, Not current, Preview), never a trace of the lines.
- **Keyboard (A-G4)** is engine-driven and looks the same: ← → step one bar (Shift: ten), reaching the first and last stored bar near the edges; Home / End jump there; another press at an edge does nothing. The live region announces "First stored bar" or "Last stored bar" once, with the date and stored values.
- **Phone:** hold 450 ms inside the 10 px slop; the chart takes the dashed hold outline (`data-hold`); values stay in the read-out row above the chart.
- `pointer-events: none` and `aria-hidden` on the layer. Contrast: 12.0:1 on dark chart-bg, 10.0:1 on light.
