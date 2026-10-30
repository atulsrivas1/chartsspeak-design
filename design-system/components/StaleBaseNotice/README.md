# StaleBaseNotice

The refusal shown when someone tries to apply an edit made against an older revision of the shared chart. Nothing is applied until the person reviews it.

**Consumer provides:** a `RefusalNotice` in its `--caution` form with `role="alert"`: the kind "Changed while you were editing.", the base and current revisions (`cs-revs`), a sentence naming who changed what in between, and two actions: Review and reapply (primary), Discard my edit (quiet).

- Never auto-merge silently. Reapply opens the same "what will change" preview as `ProposalPreview`, computed against the current revision.
- Name the intervening edits by person or agent and action. Never just say "a conflict occurred".
- The person's edit is kept locally until they choose. Leaving the screen asks before discarding it.
