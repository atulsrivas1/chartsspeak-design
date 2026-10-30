# StatusFooter

The polite live region at the bottom of the page. It announces results ("Workspace saved") and offers retry/resolve when an outcome is uncertain.

**Consumer provides:** a `cs-footer` with `role="status"` and `aria-live="polite"`, one `cs-footer__msg` (`--good` or `--caution`) and, for uncertain outcomes, Check again and Resolve buttons.

- One message at a time, and the newest wins. Messages say what happened to which named action.
- Uncertain outcomes never auto-dismiss.
