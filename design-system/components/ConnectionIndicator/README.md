# ConnectionIndicator

A dot plus a word for the workspace connection, shown in the `TopBar` only. Shape varies with state (filled, ring, square), so it never relies on colour.

**Consumer provides:** a `cs-conn` with a modifier (`--reconnecting`, `--disconnected`, `--signin`) and the word, inside an element with `role="status"`.

- Always show the word. The dot alone is never enough.
- Connection says nothing about the data. "Connected" sits beside "Synthetic" without contradiction, and "Live" is never shown.
- Reconnecting shows the attempt count and has no button. It recovers by itself.
