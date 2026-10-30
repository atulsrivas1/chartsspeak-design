# Answers for engineering (round 2)

Answers to the eight questions in the PO's round-2 request. The numbers were computed from `tokens.json`: WCAG 2 contrast ratios, and CIE76 colour difference (ΔE) after simulating full protan, deutan and tritan vision (Machado 2009, severity 1.0).

## 1. How many participant identities does colour support?

**Shape separates people from agents; colour separates people from each other, up to four.**

- People are circles (`cs-avatar--person` for you, `--p1…p4` for others) with a `presence-1…4` ring. Agents are squircles with the `accent` ring (`cs-avatar--agent`) and a small badge with the initials of the person they act for (`cs-avatar__via`).
- Colour carries identity for **four** invited people. The fifth person on gets a neutral `border-control` ring plus a number badge (`cs-avatar__num`). Initials and a name are always present, so identity never depends on colour.
- Agents are not colour-coded against each other: they share the accent ring and are told apart by name and initial. This keeps the accent meaning "an agent did this".
- Tokens: `presence-1` #9aa6ff / #4a55c8, `presence-2` #cc79a7 / #a8507f, `presence-3` #f0e442 / #7a6f00, `presence-4` #f6745a / #7d0624 (dark / light). Each passes 3:1 as a ring on every surface in both themes (lowest: 4.37 light, 5.39 dark). Across all pairs of the four, the smallest colour difference is ΔE 30 in each theme, under normal, protan, deutan and tritan simulation alike. A fifth colour could hold the same separation (a purple such as #983df4 / #590560 does), but colour stops at four on purpose: past four, people stop remembering which colour is whom, and more ring colours start competing with the chart's series colours. Adding a fifth later is a token change, not a redesign.

## 2. Which chart-affecting values are personal and which shared?

**Personal (never shared, never in undo):** theme, candle colours, gridlines, event-marker visibility, price scale (Auto/Log/%/Lock), visible range, pan/zoom, crosshair, pane heights, rail open or collapsed, and "Hidden in your view" for any item or author.

**Shared (attributed, undoable):** indicators and their presets, drawings, notes, assistant markers, benchmarks in comparison, evidence.

Confirmed: none of `ChartSettings` travels as shared state. Following someone (`FollowBanner`) copies their personal view live, but never writes it to yours.

## 3. Light theme: which chart tokens differ, and do the candles still separate?

Every `chart-*` token has its own light value (see `tokens.json`). Contrast against `chart-bg`:

| Token | Dark (on #0c0f13) | Light (on #ffffff) |
|---|---|---|
| chart-axis | 6.34 | 6.36 |
| chart-crosshair | 12.03 | 9.95 |
| chart-up (hollow) | 8.32 | 5.19 |
| chart-down (filled) | 8.53 | 3.87 |
| chart-series-1…5 | 5.61–15.71 | 5.10–18.03 |
| chart-event-split / dividend / earnings | 7.72 / 10.62 / 9.23 | 4.59 / 5.34 / 6.36 |
| chart-selection | 12.00 | 5.20 |
| chart-grid | 1.18 | 1.18 (decorative by design) |

Every mark meets the 3:1 minimum for graphics in both themes.

**Up versus down is distinguishable for colour-blind viewers.** ΔE between up and down after simulation:

| Pair | Normal | Protan | Deutan | Tritan |
|---|---|---|---|---|
| Blue/orange, dark | 113 | 101 | 111 | 87 |
| Blue/orange, light | 115 | 92 | 108 | 102 |
| Green/red (opt-in), dark | 100 | **18** | **19** | 115 |
| Green/red (opt-in), light | 95 | **13** | **27** | 108 |

Green/red collapses for protan and deutan viewers, which is why it is opt-in and why hollow-up / filled-down is kept in both modes.


**Interface contrast audit (both themes).** These are the lowest ratios for each pairing in use (WCAG 2):

| Foreground | On | Need | Dark (lowest) | Light (lowest) |
|---|---|---|---|---|
| `ink` | surface-000 / 100 / 150 / 200 | 4.5:1 | 13.50 | 15.44 |
| `ink-muted` | surface-000 / 100 / 150 | 4.5:1 | 5.96 | 5.86 |
| `accent-text` | surface-000 / 100 / 150 | 4.5:1 | 11.28 | 5.72 |
| `on-accent` | accent, accent-soft | 4.5:1 | 10.44 | 5.20 |
| `ink` | accent-wash | 4.5:1 | 11.93 | 15.81 |
| `caution` | surfaces, caution-wash | 4.5:1 | 9.64 | 5.27 |
| `good` | surfaces, good-wash | 4.5:1 | 8.70 | 4.68 |
| `refusal` | surfaces, refusal-wash | 4.5:1 | 8.03 | 5.32 |
| `ink` | caution-wash / refusal-wash | 4.5:1 | 12.62 | 15.07 |
| `border-control` | surface-000 / 100 / 150 | 3:1 | 3.35 | 3.39 |
| `focus` | every surface | 3:1 | 9.12 | 4.46 |
| `surface-000` on `caution` (count badge) | | 4.5:1 | 12.00 | 5.47 |

`ink-muted` also passes on the hover and wash surfaces: 5.44 / 5.44 on `surface-200`, 4.81 / 5.58 on `accent-wash` and 5.09 / 5.66 on `caution-wash` (dark / light). No pairing in use fails in either theme.

## 4. Is the phone Chart/Conversation switch final? What is the minimum chart height with the keyboard open?

Yes, the switch is final for phone (760px and below). With the keyboard open on the Conversation screen, the chart is not shown, so there is no conflict. If the person opens a chart from a reply ("Show on chart"), the keyboard closes first.

In landscape phone and in any case where the chart and keyboard share the screen, the minimum chart height is **160px** (enough for about 4 gridlines and a readable candle). Below that, show the `EmptyState` "Rotate or close the keyboard to see the chart" and never draw a squashed chart.

## 5. What does the preview during drag/zoom look like, and how does it differ from "Not current"?

- **Preview** (before the engine redraws after a gesture): the frame moves with the pointer at full opacity, with no veil, plus a small `Preview` tag at the top left in `ink-muted` on `surface-100`. The meta row reads "Preview". It lasts only while the gesture is in progress plus the redraw (target under 300ms after release). Values in the legend are hidden, showing "—", because they would be wrong.
- **Not current** (reconnecting, failed, sign-in): the frame stays still under `veil-retained`, with the `ChartStateOverlay` card and a timestamp.

The rule: preview means "you are moving it, it will catch up", while the veil means "this is old". Never veil during a normal gesture, and never show a Preview tag when the connection is the problem.

## 6. Should the local crosshair look different from the engine-drawn one?

No. It looks identical (`chart-crosshair`, 1px, dash 3 3), so when the engine's point frame paints, the two lines coincide and people never see two crosshairs. **Corrected 30 Oct:** an earlier version of this answer gave the local crosshair its own axis value tags. That breaks the content rules in `ARCH-geometry-zoom-px.md` section 5: the local overlay shows no price, time or value of any kind. Values appear only in the engine read-out. See `LocalCrosshair` and board 44.

## 7. Which components can ship hidden, and which need a disabled state with an explanation?

**Hide when the feature doesn't exist** (no trace in the interface): chart-type options beyond Candles, interval options beyond what is stored, drawing tools beyond lines, `Presence`, `FollowBanner`, `ConversationScope`, `InviteDialog`, `PhonePairing`, `AgentGrants`, the People tab, `AuthorFilter` with one author.

**Show disabled with a reason** (the feature exists, but not right now or not for you): Undo/Redo (with the action name and the reason), Indicator when the pane cap is reached, editing controls while reconnecting ("Paused until the chart returns"), Export and editing in the public demo (one line: "Read-only demo"), and role-gated actions for viewers ("Viewers can't edit").

The rule: if the person could make it available, explain how. If nobody can yet, hide it.

## 8. Delivery format and motion under reduced motion

**Format:** each component is markup plus tokens: `components/<Name>/preview.html` (markup using `cs-*` classes), `components/bundle.css` and `tokens.json` / `tokens.css`. Screens are shown at one breakpoint each. The responsive rules live in `AppShell` (container queries at 1440 / 1180 / 1024 / 760), so engineering builds the states once and the shell rearranges them. Breakpoint-specific states are drawn only where the layout changes meaning: the tablet drawer and the phone screens.

**Motion:**

| Motion | Default | Reduced motion |
|---|---|---|
| Colour and background transitions (hover, pressed) | 150ms ease-out | 0ms |
| Drawer open and close | 200ms ease-out, transform only | 0ms (appears in place) |
| Dialog appear | 150ms fade | 0ms |
| Veil on, after the 300ms delay | 150ms fade | 0ms |
| Toast in/out | 200ms | 0ms; stays until read or dismissed |
| Agent step completes | none (text change only) | none |
| Countdown, live log | text updates only | text updates only |

Never animate chart data, and never use motion to convey a state on its own.
