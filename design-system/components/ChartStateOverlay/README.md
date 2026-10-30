# ChartStateOverlay

The state card over a retained, veiled frame, so the last picture never reads as current. It is paired with the meta-row status (`cs-meta`).

**Consumer provides:** the `cs-chart` wrapper holding the engine canvas, a `cs-chart__veil` (`veil-retained`) and a `cs-overlay` with the state eyebrow, the sentence, the frame's time and at most one action; the matching `cs-meta` status text.

| State | Overlay modifier | Eyebrow | Action |
|---|---|---|---|
| Updating, over 300ms | none | Updating | none |
| Reconnecting | `--caution` | Not current | none (shows the attempt count) |
| Sign-in needed | `--caution` | Not current | Sign in |
| Failed | `--refusal` | Failed | Retry drawing |
| Disconnected | `--refusal` | Not current | Reconnect |

- Always state the frame's timestamp. "Not current" is said in words, not just by the dimming.
- Below 300ms of updating, show no veil and no card, only the meta row, to avoid flicker.
- During a drag, show a `cs-chart__preview` tag reading "Preview" at the top left, with no veil.
- Never replace the frame with a placeholder chart, and never blank it on a transient error.
