# PinnedSnapshot

Says which chart revision an agent's analysis was computed on. Every result, review and handoff carries one, so nobody compares answers made on different data without knowing it.

**Consumer provides:** the revision, the time it was taken, and (when the chart has moved on) how many shared changes came after it.

- Current: neutral, "Pinned to r16 · 20:31 ET".
- Behind: `caution`, "r16 · chart is now r19, 3 changes since", with a separate "Re-run on r19" action. It never updates itself.
- A review is always computed on the same pin as the result it reviews. If the pins differ, the review says so and does not give a verdict.
