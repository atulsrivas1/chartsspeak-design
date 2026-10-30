# AppShell

The frame every ChartsSpeak screen lives in: top bar, title block, the chart panel filling the remaining height, the docked assistant rail, and the status footer. It lays itself out from its own width (container queries), so it needs no page-level breakpoints.

**Consumer provides:** a sized parent (the shell fills `height:100%`), and these regions in order: `TopBar`, an optional `DemoBanner`, then `cs-shell__body` holding `cs-shell__main` (`TitleBlock`, then a `cs-panel` with `ChartToolbar`, a split `cs-meta`, the `cs-chart` canvas, a `cs-inforow` and an optional `cs-strip`), `cs-rail` and `cs-railbar`, then `StatusFooter` and `cs-shell__switch`. State goes in two attributes: `data-rail="collapsed|open"` and, on phone, `data-screen="chart|conversation"`.

| Width | Rail |
|---|---|
| ≥1440 | docked 390px |
| 1180–1439 | docked 356px |
| 1024–1179 | docked 320px |
| desktop + `data-rail="collapsed"` | 56px icon strip; the chart takes the width |
| 761–1023 | icon strip; `data-rail="open"` shows the rail as a 320px drawer over the chart |
| ≤760 | Chart and Conversation screens, switched from the bottom |

- The chart panel is the only thing that grows. The page never scrolls; the rail body does.
- Rail open or closed is personal view: it is remembered per person and never enters undo.
- The drawer does not dim the chart, so you can read the chart while you talk about it. It closes with Escape or the active strip icon, and closing it never stops a task.
- The "On this chart" strip lists what is drawn on the shared chart, with who added it. Selecting an entry highlights it on the canvas.
