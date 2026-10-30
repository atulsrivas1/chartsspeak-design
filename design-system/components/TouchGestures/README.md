# TouchGestures

The touch model for the canvas on phone and tablet, kept in Settings › Shortcuts. On first chart open, phone shows only a one-line `cs-touchhint` above the Chart/Conversation tabs ("Hold for values · drag to pan · pinch to zoom", dismissable), never a card over the chart it is teaching.

**Consumer provides:** a list of `cs-gesture` rows (icon, gesture in bold, what it does).

- **Drag** pans and **pinch** zooms time. **Press and hold** (400ms) shows the crosshair with a `cs-readout` above the finger; slide to move it, lift to leave it, tap empty space to clear it.
- Drawing on phone uses `DragHandle`s (44px) placed by tap, never freehand. Nudge buttons appear above the selected anchor.
- Every gesture has a button equivalent (range buttons, Reset view, nudge), so nothing needs a gesture to work.
