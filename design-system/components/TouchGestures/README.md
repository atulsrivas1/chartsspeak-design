# TouchGestures

The touch model for the canvas on phone and tablet, shown once on first chart open and kept in Settings › Shortcuts.

**Consumer provides:** a list of `cs-gesture` rows (icon, gesture in bold, what it does).

- **Drag** pans and **pinch** zooms time. **Press and hold** (400ms) shows the crosshair with a `cs-readout` above the finger; slide to move it, lift to leave it, tap empty space to clear it.
- Drawing on phone uses `DragHandle`s (44px) placed by tap, never freehand. Nudge buttons appear above the selected anchor.
- Every gesture has a button equivalent (range buttons, Reset view, nudge), so nothing needs a gesture to work.
