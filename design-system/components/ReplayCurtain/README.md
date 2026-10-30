# ReplayCurtain

What the chart shows during replay. Revealed bars are drawn normally (no dimming, unlike the retained-frame veil); the unrevealed part is covered by a hatched curtain with a dashed `caution` edge at the replay date.

**Consumer provides:** the replay date, the curtain's left edge, and the hidden range for the label.

- **Different from "Not current":** the veil dims a stale frame the person didn't choose. Replay is chosen and its bars are accurate up to the edge, so they stay at full strength; the tag reads "Replay · 14 Mar 2026" in `caution`.
- Drawings, markers and evidence dated after the replay date are hidden and counted ("2 drawings after 14 Mar hidden").
- **The assistant only sees revealed bars.** Answers during replay are pinned to the replay date (`PinnedSnapshot`) and say so; the assistant can't mention anything after it.
- Indicators are computed only from revealed bars, so an SMA near the edge is what it was on that date.
