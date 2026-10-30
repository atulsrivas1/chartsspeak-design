# TemplateMenu

Saves and applies a chart setup: indicators, panes and layout. Templates never hold data or drawings, so applying one can't move your analysis onto another symbol.

**Consumer provides:** templates grouped as Yours and Workspace (with the author), what each one contains, templates that can't be applied (and why), and Save current as template.

- Each option says what it contains, in words ("SMA 50, SMA 200 · 1 pane"), so nobody applies a template blind.
- A template that needs an indicator that isn't stored is shown disabled with "Needs RSI 14 for QQQ, not stored". It is never partly applied.
- Applying a template to a shared chart is a shared edit: it goes through the normal undo ("Undo apply Trend set"), and an agent applying one sends a `ProposalPreview` instead.
- Workspace templates are visible to everyone in the workspace; only their author or an owner can change them.
