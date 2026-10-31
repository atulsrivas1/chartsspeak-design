# WorkspacePanes

The three-pane working screen: menu, chat and chart, with an optional people row under the top bar.

- `cs-shell--panes` on the shell, then `cs-people` (optional), then `cs-wpanes` holding `cs-wpane--menu`, `cs-wpane--chat` (also `cs-rail`, so message and card styles apply) and `cs-wpane--chart`.
- Collapse by setting `data-collapsed="true"` on a pane. A collapsed pane is 56px wide, keeps its icon button and a vertical label, and hides its body. The chart pane has no collapsed state.
- A collapsed chat carries `cs-iconbtn__count` on its icon when something awaits review. Do not omit it.
- Menu rows use `cs-navrow`. The current chart is `aria-current="true"` (surface-200 plus an ink edge, never accent).
- People: `cs-peoplebtn` in the top bar opens `cs-people`. People are circles with presence rings, the assistant is a squircle. `cs-teamvideo` is the owner's setting and is off by default; `cs-tiles` appears only when it is on.
- Chat log: `cs-chatlog` anchors to the newest message.
- Phone (container width 760px and below): one pane at a time using `data-screen="menu|chat|chart"` and the bottom `cs-tabbar3`.
- Keyboard: `[` menu, `]` chat, `f` focus. Every collapse button has `aria-expanded` and an `aria-label`.
