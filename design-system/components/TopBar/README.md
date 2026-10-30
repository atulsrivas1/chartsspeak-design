# TopBar

The app's top row: the `cs-wordmark`, then (once a workspace is open) the workspace title and its save state, the Private/Shared/Demo tag, the `ConnectionIndicator` and the owner avatar.

**Consumer provides:** the workspace title, the save state, the tag text ("Private", "Shared · 3 people", "Read-only demo"), the connection state and the person's initials. The bar is `surface-100` with a `border-200` bottom edge and `space-30` gutters (`space-16` on phone).

- **The workspace title lives here on desktop and tablet**, as `cs-topbar__title` (15/20 semibold, truncates with an ellipsis), after a `cs-topbar__sep`. This replaces the page-level `TitleBlock` on workspace screens, giving the chart about 80px more height.
- Connection state lives here and nowhere else. The data class never appears in this bar: it lives in the chart toolbar only.
- The name is always the `cs-wordmark` markup, with `role="img"` and `aria-label="ChartsSpeak"`. There is no separate logo mark or icon.
- On phone the bar has no room for the title, so phone screens keep `TitleBlock`.
