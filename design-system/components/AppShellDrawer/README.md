# AppShellDrawer

Tablet with the rail open as a drawer over the right of the chart.

**Consumer provides:** `data-rail="open"` on the shell and `aria-pressed="true"` on the strip button for the open tab; focus moves into the drawer and returns to the button when it closes.

- The drawer sits over the chart without dimming it.
- Escape or the pressed strip icon closes it. Closing it never stops a running task.
