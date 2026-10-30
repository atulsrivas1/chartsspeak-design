# AgentLiveWork

Watching an agent work without interrupting it: a step list that fills in as the agent goes, with Stop always visible.

**Consumer provides:** a `cs-card` with `aria-live="polite"`, the task line, a `cs-steps` list (each step `data-state` done/now/next, with a timestamp for done steps), and an attribution line.

- Watching never blocks: say "nothing is locked". Your own edits continue, and the agent's output arrives as a `ProposalPreview` when it changes the shared chart.
- Steps describe checks and actions in plain words. Data values only appear in the final `ResultCard`, never in the live log.
- Announce only step completions, not every update.
