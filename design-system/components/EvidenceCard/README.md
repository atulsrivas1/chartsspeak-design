# EvidenceCard

A saved engine observation that reopens exactly as it was, labelled "as of then" so it never passes for the current chart.

**Consumer provides:** a `cs-card` with a title, the Snapshot `DataClassBadge`, a `cs-evidence__asof` line (time, data class, adjustment), the observation in `cs-pre`, and two actions: Reopen as saved (default) and Show on current chart (quiet).

- "As of" is always visible. The two actions are separate because they mean different things: reopening restores the old frame, while showing on the current chart re-draws the observation on today's data.
- A reopened snapshot keeps the Snapshot badge in the toolbar until you leave it.
