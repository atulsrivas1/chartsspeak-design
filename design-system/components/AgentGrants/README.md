# AgentGrants

The grant editor for one agent: whether it may apply edits or only propose them, what data it can read, step/time/spend limits, expiry, and revoke.

**Consumer provides:** a `cs-card` headed by the agent (with its `cs-avatar__via` delegate badge) and an expiry badge, a list of `cs-grant` rows (name, one-line consequence, control), and a footer with Revoke all grants (quiet, refusal-coloured) and Save grants.

- Defaults are safe: "Propose only", this workspace, limits on, expiry 7 days.
- Each row says what happens at the limit ("Stops and asks"). Spend uses `cs-meter`, turning `caution` at 75%.
- Revoke opens a confirmation that names the running tasks it will stop. Revoking never deletes past work; that stays attributed.
- Agent setup (name, role, model detail) is the same card's header menu; the model is shown as a read-only detail, never as a choice that changes results silently.
