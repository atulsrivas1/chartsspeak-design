# EmptyState

The centred empty state inside the chart panel for: an empty workspace, a symbol with no stored data, or a chart that is still opening.

**Consumer provides:** a `cs-empty` block with the symbol (or a short word) in `cs-empty__sym`, a headline, one sentence that says what was not done, an optional `CommandCopy`, and one action.

- Say "nothing was fetched or estimated". Never show an empty axis or a placeholder chart.
- Variants: "Your workspace is empty" (first run), "<SYMBOL> isn't stored yet", "Opening saved chart" (no command, no action).
