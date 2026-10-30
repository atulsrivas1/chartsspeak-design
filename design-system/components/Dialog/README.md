# Dialog

A modal dialog over a blurred `scrim`. It is used for sign-in and confirmations, and only for decisions that block the whole workspace.

**Consumer provides:** a `cs-scrim` wrapping a `cs-dialog` with `role="dialog"`, `aria-modal`, a labelled `cs-dialog__title`, body copy and right-aligned actions (primary last); focus moves into it and returns to the opener.

- Escape closes it unless it is the sign-in dialog when sign-in is required.
- Say what is kept ("Your saved analysis is kept") whenever a dialog interrupts work.
- Refusals and task results never open a dialog. They go in the conversation or in `StatusFooter`.
