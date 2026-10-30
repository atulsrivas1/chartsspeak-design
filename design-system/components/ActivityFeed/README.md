# ActivityFeed

The Activity tab: what changed, by whom, and what needs you, newest first and grouped by day, with filters.

**Consumer provides:** a filter row of `ToggleChip`s (Needs me with a `cs-countbadge`, Agents, People, Chart changes) and a `cs-feed` list. Each `cs-feed__item` has an avatar, a sentence with the actor in bold, a time, and optional actions. Use `data-attention="true"` for items that need the viewer, `data-unread="true"` for unseen ones.

- Entries name actions, never data values. "Ana R. removed SMA 200", not the series' numbers. The log is bounded (show the retention period).
- "Needs me" is the default filter when it has items. The rail tab shows the same count badge.
- Solo users see a quieter feed: their own actions are collapsed into one line per session.
