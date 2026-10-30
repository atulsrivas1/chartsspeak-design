# TaskCard

One assistant task, with its state in words and a glyph: queued, running, needs input, awaiting approval, completed, stopped or failed.

**Consumer provides:** a `cs-card` whose head holds a `cs-task__state` (modifier `--running`, `--attention` for needs input/awaiting approval, `--done` for completed, `--failed`; none for queued and stopped), the task text, an `AttributionChip`, and the actions for that state.

- Stop is visible for as long as a task is queued or running. If Stop is not acknowledged, say "Stop not acknowledged" in the `StatusFooter` with a retry.
- Awaiting approval offers Apply and Decline. Needs input points to the composer.
- A completed task becomes a `ResultCard`. Do not keep both.
