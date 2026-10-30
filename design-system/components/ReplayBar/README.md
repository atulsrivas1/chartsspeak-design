# ReplayBar

Bar replay on stored daily data: the chart shows bars up to a chosen date and reveals the rest one at a time. It sits under the chart, replacing the info row while replay is on.

**Consumer provides:** the replay position (bar n of total, with its date), play state, speed, and the revealed fraction.

- The words "Replaying · not current" are always visible in the bar and on the chart (`ReplayCurtain`). Replay is a past view; it must never be mistaken for the current chart.
- Controls: back to start, step back, play or pause, step forward, speed (1×, 2×, 5×), Jump to date, Exit replay. Left and right arrow keys step; Space plays and pauses.
- Replay is personal: it changes only your view. Other people keep seeing the current chart, and the presence strip says "Monika is replaying to 14 Mar".
- Under reduced motion, Play steps one bar per second without animating between bars.
- **Editing is off during replay.** Undo, Indicator, Compare and drawing are disabled with "Exit replay to edit": they change the current shared chart, which you aren't looking at. Interval and chart type stay available, because they only change your view.
