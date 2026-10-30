# DragHandle

A 44px round handle for drawing anchors, ringed in `anchor`, with nudge buttons as the keyboard and touch equivalent.

**Consumer provides:** `<button class="cs-handle">` positioned over the anchor point, with an `aria-label` naming the anchor's date and price; `aria-grabbed="true"` while dragging; an optional `cs-nudge` group.

- The handle is the 44px target; the visible dot stays 10px, so the canvas is not covered.
- While dragging, the canvas shows the "Preview" tag (see `ChartStateOverlay`). Do not show the new position as applied until the engine confirms it.
- Drawing tools are a development-build feature; their final scope is not yet defined.
