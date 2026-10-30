# FollowBanner

A strip across the top of the chart panel while you follow someone's view (W2). Its bottom edge takes that person's presence colour.

**Consumer provides:** a `cs-follow` with `role="status"`: the person's avatar and name, one sentence on what follows, and Stop following.

- Following moves only personal view (zoom, pan, crosshair, panel visibility). Shared analysis is always the same for everyone.
- Any pan or zoom by you stops following and says so in the `StatusFooter`. Escape also stops following.
- An independent view, the default, shows no banner.
