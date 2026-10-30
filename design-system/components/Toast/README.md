# Toast

A short message in the bottom-right corner of the chart area for things that need attention now or that you'd want to know about immediately.

**Consumer provides:** a `cs-toast` (`role="status"`) with the actor's avatar, a title, one line of detail, and one action or a Dismiss button; stack them in `cs-toasts`, at most 3.

When to use what:

| Event | Toast | Activity only | Digest |
|---|---|---|---|
| Proposal waiting for you, agent paused at a limit, conflict on your edit | yes, stays until handled | yes | no |
| Your agent finished, someone joined | yes, 6s (paused on hover/focus) | yes | no |
| Others' routine edits | no | yes | daily, if enabled |
| Anything while Quiet mode is on | only "needs you" items | yes | yes |

- Toasts never carry data values, and never auto-dismiss when they need an action.
- Under reduced motion they appear without sliding and stay until dismissed.
