ChartsSpeak is an assistant-first chart workspace. You ask an assistant ("Mat") to do analytical work, and the result is drawn on the chart with the evidence behind it. The interface has one job: make the work **visible, attributable and checkable**, and never let it look more current, more live or more certain than it is. It never recommends trades or predicts prices.

When a choice is unclear, take the more honest option over the more polished one.

## Content fundamentals

- **Voice:** plain, exact, calm. Say what happened and what to do next, in that order. "SMA 50 for SPY is not stored. Run the feature utility to create it." Avoid "Oops", "Unfortunately" and exclamation marks.
- **Person:** the product speaks as "you" to the analyst. The assistant speaks by name in the first person ("I compared…") only inside its own cards.
- **Casing:** sentence case everywhere, buttons included ("Sign in", "Show on current chart"). Uppercase only in `label` eyebrows ("YOUR ANALYTICAL WORKSPACE").
- **Name the action, not the gesture.** Undo says "Undo add SMA 50", not "Undo". Retry says what it retries.
- **No emoji, no exclamation marks, no forecast words** ("will", "target", "buy", "bullish signal"). Describe what is in the stored data: "crossed above", "closed below".
- **Assistant answers come in three labelled parts, always in this order:** Calculated fact, then Interpretation, then Limitations. Omit an empty part. Never merge them into one paragraph.
- **Numbers:** tabular figures (`numeric` style), units after the value, dates as "14 Mar 2026", times as 24-hour New York time with "ET" the first time it appears in a view.

### Data-honesty vocabulary

These words are fixed. Use them exactly, through `DataClassBadge`, `ConnectionIndicator` and `RefusalNotice`, and never paraphrase them:

| Axis | Allowed values | Shown by |
|---|---|---|
| Data class | Synthetic · Stored daily · Stored 1-minute · Delayed | `DataClassBadge` in the toolbar and the demo banner |
| Adjustment | Split-adjusted, not dividend-adjusted · Raw (unadjusted) | `DataClassBadge kind=adjustment`; data run on hover |
| Coverage | Stored through 28 Oct 2026 | Caption under the title |
| Connection | Connected · Reconnecting · Disconnected · Sign-in needed | `ConnectionIndicator` in the top bar only |
| Save state | Saved · Saving · Needs attention · Local | `SaveStateChip` in the title block |
| Refusal | Not stored · Stale · Basis mismatch · Not permitted, nothing changed | `RefusalNotice` |

Data class and connection are **different axes in different places**. A healthy connection never upgrades a data class, and "Live" does not appear in the product until live data exists.

## Visual foundations

**Colour.** The product is neutral first, with one hue. Build every screen from `surface-000` (page), `surface-100` (panels), `surface-150` (rail, toolbars, cards in the rail) and `surface-200` (hover/pressed only). Use `border-200` for panel edges, `border-100` for hairlines inside and `border-control` for anything you can operate. Text is `ink`, with `ink-muted` for secondary text. Spend `accent` on the next action, the selected tab and "on" states; one accent fill per region. Selected rows get `accent-wash` with `ink` text. State hues are only `caution` (stale, reconnecting, needs attention, proposed), `good` (saved, connected, completed) and `refusal` (refused, failed, not permitted), each on its `-wash`. Every state also carries a word and a glyph, never colour alone.

**Themes.** Dark is shipped and stays the first theme; light is an equal. Set `data-theme="dark|light"` on `<html>`. Every token is defined in both themes, and you never hard-code a hex value.

**The chart canvas is not CSS.** The engine draws candles, axes, grid, crosshair and indicator lines. Hand the engine/pack the `chart-*` tokens (resolved per theme) as its theme. Up candles are `chart-up`, drawn hollow; down candles are `chart-down`, drawn filled. The pair is blue/orange so that red-green colour blindness does not hide direction, and the hollow/filled shape carries direction without colour. Indicator lines take `chart-series-1…5` in order. Benchmarks reuse series 5, 2, 3, 4 **dashed**, so a benchmark never reads as an indicator. Event markers are `chart-event-split|dividend|earnings`, and each carries its letter (S, D, E), because the old grey/green/red key was colour-only. Someone who prefers green/red can switch to `chart-up-conventional` / `chart-down-conventional` in `ChartSettings`; it is opt-in only, and hollow/filled stays. The exact object the engine receives is in the Engine theme hand-off section.

**Type.** Use one family, `sans` (Inter, falling back to the system stack). `mono` is for evidence and data-run ids only. The scale is `title-page` 27, `title-panel` 19, `heading` 15, `body` 13 (base), `small` 12, `caption` 11, `label` 11 uppercase +0.06em, `numeric` 12 tabular, `code` 12 mono. **Nothing is smaller than 11px**, which retires the 7–9px labels. Density comes from tight line heights and spacing, not from tiny type. Phone uses the same scale; `title-page` drops to 21/26.

**Spacing.** Use only `space-4 … space-30`. Page gutter is `space-30` on desktop and `space-16` on tablet and phone. Panel padding is `space-16`, card padding `space-12` and gaps between panels `space-18`.

**Layout: build every screen inside `AppShell`.** The chart gets the space and the assistant stays one glance away, the way a pro charting tool keeps the chart dominant with a docked side panel. The shell responds to its own width:

| Shell width | Rail | Notes |
|---|---|---|
| ≥1440px | docked, `size-rail-wide` | |
| 1180–1439px | docked, `size-rail` | |
| 1024–1179px | docked, `size-rail-small` | |
| any desktop width, rail collapsed by the person | `size-railbar` icon strip | gives the chart the full width; a personal-view setting, not part of undo |
| 761–1023px (`size-tablet-max`) | icon strip, with the rail as a `size-rail-small` drawer over the chart | the chart is never squeezed below a usable width; the drawer does not dim the chart |
| ≤760px (`size-phone-max`) | none: Chart and Conversation are two screens | the switch sits at the bottom within thumb reach; the toolbar scrolls sideways and its controls go back to 44px |

The chart panel always fills the height left over by the top bar, the title block and the footer; nothing scrolls the page except the rail body. There is never horizontal page overflow. Drawing tools, when they leave the demo build, get a vertical strip on the left edge of the chart panel, not a new region.

**Shape.** Corners: `radius-xs` for badges and markers, `radius-control` for controls, `radius-panel` for panels and cards, `radius-dialog` for dialogs, `radius-round` for dots, avatars and handles. Edges: use 1px borders; shadows appear only on dialogs (`shadow-dialog`) and the in-chart notice (`shadow-overlay`). Do not use gradients, glows or left-border accent cards.

**Targets and focus.** Every operable thing is at least `size-target` (44px) tall. The only exceptions are desktop toolbar icon buttons at `size-target-compact` inside a 44px row. Focus is a solid `size-focus-ring` outline in `focus`, offset 2px, on every control, and it is visible on every surface in both themes.

**Motion.** Background and colour transitions are 150ms ease-out, and the only motion is state change. Under `prefers-reduced-motion: reduce` all transitions are off. Spinners do not appear on the chart; status text is used instead.

### Chart states: a retained frame never reads as current

Whenever the canvas is not showing the current state, the last frame stays visible under `veil-retained`, with the status in words in two places:

1. The meta row status changes from `Rendered r12 · 19:58:02` to the state ("Chart updating", "Reconnecting, attempt 2", "Not current").
2. A `ChartStateOverlay` card sits centred over the veiled frame and states the state, the time of the frame you are looking at, and the one action (if any).

| State | Veil | Overlay | Action |
|---|---|---|---|
| Updating, under 300ms | none | none (meta row only) | none |
| Updating, over 300ms | yes | "Chart updating" | none |
| Preview during drag | none | a small "Preview" tag at the top left of the canvas | release to apply |
| Reconnecting | yes | "Reconnecting… your chart will return automatically." plus the attempt count | none |
| Sign-in needed | yes | "Sign in again. Your saved analysis is kept." | Sign in |
| Failed | yes | "The chart could not be drawn." | Retry |
| Disconnected | yes | "Chart disconnected." | Reconnect |

Never draw a substitute or decorative chart, and never clear the frame on a transient error.

## Assistant presence

- Everything the assistant adds is attributed with an `AttributionChip` ("Mat · 19:41"). A person's own edits show their initials. Hidden assistant additions say "Hidden in your view", which is presentation only.
- Tasks show their state with `TaskCard`, using the words queued, running, needs input, awaiting approval, completed, stopped and failed, each with a glyph. Stop is always reachable while a task runs. Escape closes a view and never stops a task.
- Evidence is a snapshot. `EvidenceCard` always shows "As of <time>" and offers "Show on current chart" as a separate, secondary action. A reopened snapshot is badged "Snapshot". It never looks like the live chart.
- Proposed changes show "Proposed, not applied" in `caution` until accepted.

## Working together (W2 and later)

Nothing in this section appears until a second person is invited. The single-person screen stays exactly as it is.

- **Person or agent is shown by shape:** people are circles, agents are squircles with the accent ring and a badge with the initials of the person they act for (`ParticipantRoster`). Colour separates up to four people (`presence-1…4`). From the fifth on, rings are neutral with a number. Status always has a glyph and a word.
- **Shared edits are never silently merged.** A stale base gets `StaleBaseNotice`, a blocked undo gets `UndoRefused`, and an agent's change waits in `ProposalPreview` with an explicit list of what will change, drawn dashed on the chart as "Proposed". Watching an agent work (`AgentLiveWork`) never locks anything.
- **Empty is honest:** `FirstRunChecklist`, `EmptyState`, `CoverageBar` and `CommandCopy` say what is not stored and give the exact utility command. They never estimate or fetch.
- **Access:** `InviteDialog` (Viewer, Editor, Owner, as proposed), `AgentGrants` (propose-only by default, with data scope, step/time/spend limits, expiry and revoke) and `PhonePairing` (one-time QR with a countdown).
- **Exports and links stay honest:** `ExportDialog` burns the data label, adjustment and "as of" date into every image (this can't be turned off), and `ShareDialog` defaults to a frozen snapshot with an audience and an expiry.
- **What needs you:** `ActivityFeed` (filters, with "Needs me" first) and `Toast` (only for things that need action or that you asked for). Quiet mode keeps solo work silent. Neither ever shows data values.
- **Personal settings:** `SettingsPage` (System/Dark/Light, candles, data defaults, notifications), `ShortcutSheet`, `TouchGestures` (press and hold for the crosshair) and `IndicatorStyle` (chart palette only, no free colour picker).
- **Who is here:** `Presence` in the top bar. Each invited person gets a `presence-1…3` ring, which is used only for their avatar, their cursor and the `FollowBanner` edge, always next to their initials and name.
- **Shared and personal are different layers.** Indicators, drawings, notes and evidence are shared and attributed (`AttributionChip`, `ObjectList`). Pan, zoom, crosshair, pane heights, scale, theme and hidden items are personal, are never part of undo, and never change anyone else's screen.
- **Following** someone moves only your personal view, shown by `FollowBanner`. Any gesture of your own stops following and says so. Independent view is the default.
- **Conversation** is Shared or Private (`ConversationScope`). Every message says which. A private task result stays private until you share it with one action.
- **Shared undo** names the person whose action it reverses ("Undo Ana's add EMA 21"), and it refuses, with that reason, if someone edited after it.
- **Several assistants (W3)** each get a name and initial in the accent ring, and their own row in `ObjectList`. Peer review appears as a second `ResultCard` attached to the first, never merged into it.
- **Agents checking each other (W3):** only a person can ask one agent to review another (`ReviewRequest`). The review is computed on the same `PinnedSnapshot`, attaches under the original, and ends in Agrees, Differs or Couldn't check. "Agrees" means the fact was reproduced, not that the interpretation is endorsed.
- **Disagreements are decided by people:** `DisagreementView` puts both answers side by side (fact, interpretation, limitations), names the kind of difference (definition, data, method, interpretation) and offers Use Mat's, Use Grace's, Keep both, or Ask. Agents never vote or settle it themselves.
- **Handoffs say what travels:** `HandoffCard` lists what moves to the next agent (question, pin, evidence, steps left, open questions) and what stays behind (private messages, personal view, the sender's grants). Nothing runs until the receiving agent's person accepts.

## Beyond one chart (P2, owner go-ahead)

- **Layouts:** `LayoutBar` picks 1, 2 or 4 charts; four is the ceiling. The layout is shared; sync (crosshair, interval, date range, symbol) is personal. Each `ChartSlot` keeps its own data label and state, and one slot is "Active" in words and outline: shortcuts, the indicator picker and the assistant act on it. Phones show one slot at a time with a symbol switcher.
- **Templates:** `TemplateMenu` saves indicators, panes and layout, never data or drawings. A template that needs something not stored can't be applied, and is never applied in part.
- **Watchlist and alerts are stored data only:** `Watchlist` shows the last stored close and its date, never a sparkline or an estimate. `AlertEditor` builds a condition that reads back as one sentence and always states "Checked after each daily update, not real-time". `AlertList` says "Can't check" rather than staying silent when data is stale. The rail switches between Assistant and Watchlist at the top, so the assistant's five tabs stay as they are. Live data is an owner decision; real-time alerts would be a separate pattern.
- **Replay is chosen, not stale:** `ReplayBar` and `ReplayCurtain` show past bars at full strength and hide the rest behind a hatched curtain, with "Replaying · not current" in words. Unlike the retained-frame veil, nothing is dimmed. Replay is personal, hides later drawings, and the assistant sees only revealed bars.

## Iconography

There is no icon set yet. The five rail icons (Conversation, Evidence, Activity, Layers, Data) are inline SVGs in `AppShell`: 20px, 1.5px stroke, round caps, coloured with `currentColor`. Each always has an `aria-label`, and a tooltip with the tab name. Elsewhere, use the few glyphs defined in `bundle.css` as text characters: ● dot for connection, ✓ good, ! caution, ⨯ refusal, ↶ ↷ undo/redo, and the S/D/E marker letters. Any icon set you add later must be single-weight outline icons at 16px with a 1.5px stroke, coloured by the text token beside them. **Brand:** the name is the logo. Write it as `cs-wordmark`: "ChartsSpeak" in `sans` weight 600, with the "sS" drawn as two interwoven S's. The S of "Charts" is in `ink`, the mirrored S of "Speak" in `accent-text`, and it passes under at the crossing with a gap.

- Use it in every page header (`TopBar`) at 15px, and in display headings with `cs-wordmark--display` (40px and up: cover, landing hero, title cards).
- Always use two colours: in one colour the SS reads as an "8". The crossing gap takes the colour of the surface behind it (`--halo`), which is `surface-100` in the top bar and `surface-000` for display.
- Keep `role="img"` and `aria-label="ChartsSpeak"` on the wrapper, so screen readers and search read the real name.
- In running text, alt text, page titles and anything typed, the name is plain "ChartsSpeak". Never use the woven SS on its own as an icon, favicon or avatar.

## Accessibility floor

- Text meets 4.5:1 on the surfaces its token note names, in both themes. `border-control`, `focus` and chart marks meet 3:1.
- The canvas has an accessible name and a text description of its keyboard use (arrows pan, + and − zoom, Escape clears the crosshair). Every number on the chart is also available as text in the legend, the hover readout or Evidence.
- Results and conflicts are announced through the polite live region in `StatusFooter`.
