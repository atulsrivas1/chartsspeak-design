# TopBar

The app's top row: the `cs-wordmark` (the name with the woven SS), a Private/Demo tag, the `ConnectionIndicator` and the owner avatar.

**Consumer provides:** the tag text ("Private", or "Read-only demo"), the connection state and the person's initials. The bar is `surface-100` with a `border-200` bottom edge and `space-30` gutters (`space-16` on phone).

- Connection state lives here and nowhere else. The data class never appears in this bar.
- The name is always the `cs-wordmark` markup, with `role="img"` and `aria-label="ChartsSpeak"`. There is no separate logo mark or icon.
- Symbol search, when it comes, goes between the tag and the spacer.
