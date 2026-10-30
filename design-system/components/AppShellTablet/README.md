# AppShellTablet

Tablet width (761–1023px): the chart keeps the width, and the rail is reached from the 56px icon strip.

**Consumer provides:** the `AppShell` markup unchanged; `data-rail="open"` and `aria-pressed` on the active strip button when the drawer is open.

- The strip is always visible, so the assistant is one tap away and the chart is never squeezed below a usable width.
- See `AppShellDrawer` for the drawer open.
