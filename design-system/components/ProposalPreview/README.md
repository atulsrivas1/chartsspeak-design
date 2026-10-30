# ProposalPreview

An agent's (or a viewer's) proposed change to the shared chart, shown as an explicit list of what will be added, removed or changed, with the same items drawn dashed on the canvas as "Proposed".

**Consumer provides:** a `cs-card` with an "Awaiting your approval" state, the proposer's attribution, a `cs-diff` list (one row per change with an Add/Remove/Change op, plus one muted "Unchanged" summary row), the base revision, and actions: Apply n changes (primary), partial apply when a removal is involved, Decline.

- Removals of someone else's work always name the owner ("yours", "Ana's") and get their own partial-apply option.
- The canvas shows proposed items dashed in `chart-selection` with a `cs-ghost-tag` reading "Proposed". They never look applied.
- If the base revision is stale by the time someone approves, show `StaleBaseNotice` instead of applying.
