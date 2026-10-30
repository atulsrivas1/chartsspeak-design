# ChartsSpeak: overview for the design-system designer

Status: working draft for an external designer. It describes what exists today and what is planned. Plans are not promises. Anything the project sources do not confirm is marked **not yet defined**. The live read-only demo is at https://pcsp-mj07qs9v.tail0b4c2c.ts.net (it currently shows real stored daily NVDA data).

## 1. What ChartsSpeak is, and for whom

ChartsSpeak is an assistant-first analytical chart workspace. A person looks at a financial chart, asks a named assistant (first one: "Mat") to do analytical work, and sees the result drawn on the chart with the evidence behind it. The product value is visible, attributable, checkable work. It does not recommend trades or predict prices.

First user: an individual chart analyst checking a reproducible technical observation (for example, where a fast and slow moving average cross), questioning the explanation, undoing the edit, and reloading to find everything intact. The owner can also use every control directly, without the assistant.

## 2. Product model

- **Assistant-first, chart workspace.** Conversation produces visible changes on the chart. Ordinary chat does not start an assistant task. Only an explicit mention or reply-to-assistant does.
- **Four layers.** (1) The engine draws the chart on a canvas using the GPU and owns chart geometry and hit-testing. (2) An SDK/viewer embeds the engine in a browser. (3) A workspace service holds identity, permissions, ordering of edits, and recovery. (4) The app is the web interface around these.
- **Pluggable data adapters.** Data arrives through adapters and a finance "pack" (declarations of what exists). Source-specific logic lives there, not in the engine.
- **The engine and pack never calculate.** All numbers shown, including indicators, come from stored values prepared offline by a separate utility. If a value is not stored, the app says so ("SMA 50 for SPY is not stored. Run the feature utility to create it.") rather than computing it or drawing a partial series. Three refusal families exist: missing, stale, and adjustment-basis mismatch.
- **Honest labelling.** Data class is always shown (synthetic, stored daily, raw vs split-adjusted) and is separate from connection state. A healthy connection never turns synthetic data into "live market data".
- **Shared analysis vs personal view.** Indicators, layers and notes are shared and attributed. Pan, zoom, crosshair and panel visibility are personal and are not part of undo.

## 3. Current features

- **Chart:** OHLC price chart with a 1D timeframe by default; one-minute and five-minute historical data is supported by the app (five-minute can be derived from one-minute rows). Whether other chart types (line, area, and so on) exist is **not yet defined** in the sources.
- **Indicators and overlays (stored presets only):** SMA 20/50/200, EMA 9/21/50 and 12/26, Bollinger 20,2, RSI 14, MACD 12/26/9, ATR 14. Overlays sit on the price pane; others get their own pane. A cap of two indicator panes at once applies, with a message on the third. Custom periods show "Not stored" and are not available. Hover shows value and source.
- **Benchmark comparison:** compare against SPY, QQQ or a sector ETF, rebased to percent from the first visible bar, legend names the benchmark, gaps shown where bars are missing. Target of up to four benchmarks per session with an "n of 4" counter. Overlays are hidden in comparison mode with a visible notice.
- **Event markers:** split, dividend and earnings markers on the correct bar (split first; dividends and earnings depend on a data-source decision). Current marker key colours: grey split, green dividend, red earnings.
- **Adjustment badge:** "Split-adjusted, not dividend-adjusted" or "Raw (unadjusted)", with the data run shown on hover.
- **Timeframes:** daily is the default release scope; intraday is a follow-up.
- **Crosshair and hover:** a cursor reports bar values and indicator values. Today each hover step is rendered by the engine and returned as a picture, so it can feel slower than a typical charting site (measured roughly 57 ms locally and about 200 to 500 ms remotely).
- **Zoom and pan:** wheel zoom, drag pan, keyboard (arrow keys pan, plus/minus zoom, Escape clears the crosshair).
- **Assistant and chat:** conversation rail, mention-based assignment, task states (queued, running, needs input, awaiting approval, completed, stopped, failed), Stop, and responses split into calculated fact, interpretation, and limitations.
- **Evidence:** saved engine observations that can be reopened later exactly as they were, with a separate "show on current chart" action.
- **Undo/redo:** guarded; each button names the action it will reverse; it refuses if another edit intervened.
- **Collaboration and shared views:** a single owner and one assistant today. Invited people, shared versus private conversation, followed views and phone pairing are planned (see section 7). Saved and recoverable workspaces exist; personal view is kept apart from shared structure.
- **Drawings (demo build):** anchor-based drawing tools, with drag handles, nudge buttons, saved state and image export are in a development demo build; their final scope is **not yet defined**.
- **Real vs mock data:** real stored data is local and private by default. The public demo is read-only, and shows delayed, stored daily data for a short fixed list of symbols, with a banner: "Delayed, stored daily data, read-only, for demonstration only. Not investment advice." Visitors can look, hover, pan and zoom; they cannot change data, save, export, or message the assistant.

## 4. UI inventory

**Regions (desktop):**
1. Top bar: brand mark and name, "private" tag, connection indicator (dot plus text).
2. Demo banner (public demo only): data-class statement, and a chart selector when several are offered.
3. Title block: small caps label "YOUR ANALYTICAL WORKSPACE", large title (symbol and date range), a "Saved / Saving / Needs attention / Local" chip, one line of data description, a Reconnect button.
4. Chart panel: toolbar (symbol, interval, "OHLC", adjustment badge, Undo, Redo, an add-indicator button in the synthetic workspace), optional tool rows in the drawing demo, a meta row (legend and render status such as "Rendered r12" or "Chart updating"), the chart canvas, a bottom info row, and an analysis strip.
5. Right rail (about 320 to 390 px wide): heading and participant avatar, tab bar, scrolling body, composer at the bottom. Tabs: Conversation, Evidence, Activity, Layers, Data (plus Drawings, State, Export in the drawing demo).
6. Status footer: polite live region for results ("Workspace saved"), with retry/resolve buttons when a request outcome is uncertain.

**Components in use:** primary / default / quiet buttons, tab buttons with a pressed state, toggle chips, text input and textarea composer, select, checkbox rows, cards (assistant card, list card, task card, result card), badges and tags, a modal dialog, a sign-in dialog over a blurred backdrop, an in-chart notice overlay, a definition-list "facts" block, preformatted evidence blocks, and 44 px circular drag handles.

**Chart-state notices (shown over the last drawn frame, which stays visible but dimmed):**
- Loading / updating: "Chart updating" (header label), "Updating indicator..." (status).
- Reconnecting: "Reconnecting... your chart will return automatically." with an attempt counter. No button; recovers by itself.
- Needs sign-in: "Sign in again" with a Sign in button; saved analysis is kept.
- Failed: "The chart could not be drawn" with a Retry button.
- Disconnected: "Chart disconnected".
- Empty / opening: a centred empty state with a large symbol, headline and one sentence ("Opening saved chart" or "Unlock the workspace...").
- Other messages: "Overlays hidden in comparison mode", "Not stored. Request via utility", the three stored-data refusals, "Proposed, not applied", "Not permitted, nothing changed", "Stop not acknowledged".

**Interaction behaviour:** hover shows a crosshair and values; drag pans; wheel zooms; keyboard equivalents exist; focus ring is a 2 px teal outline; transitions are minimal (0.15 s background) and are disabled under reduced-motion. Drag handles are 44 px targets.

**Responsive:** three widths. Wide desktop (rail 390 px), desktop (rail 356 px), small desktop (rail 320 px), and phone (760 px and under) which switches between Chart and Conversation screens with a two-button tab bar and a horizontally scrolling tool row. Tablet drawer behaviour is specified but not separately implemented as far as the sources show.

## 5. Current look, as implemented

- **Theme:** dark only. There is no light theme or theme switch in the app today. The page declares a dark colour scheme. A light theme is **not yet defined**.
- **Colours (hard-coded hex values, no named tokens yet):** page background near-black blue-grey (#0c0f13); panels (#101216, #11171c); borders (#222a31 to #303940); body text (#e4e9ed); muted text (#89969f); accent mint/teal for primary action, focus and selected states (#a5e7df, #72ded5); amber for warnings and drawing anchors (#f1c76b, #a6946b); green for demo/good state; a muted red-brown for refusals. Event key colours are grey, green and red as above.
- **Type:** Inter, falling back to the system sans stack. Base size 13 px. Page title 27 px; panel headings 15 to 23 px; most body and control text 10 to 12 px; some labels as small as 7 to 9 px with wide letter-spacing (these are below common legibility minimums and are a candidate for review).
- **Shape and spacing:** corner radii 4 to 12 px (buttons 7, panels 10, dialogs 12), 1 px borders, page gutters 30 px (16 on phone), gaps in a loose 6/8/12/18 range. No formal spacing scale exists.
- **Controls:** minimum 44 px tall for buttons and inputs.
- **Tokens:** none exist as CSS variables or a token file. Everything is literal values in one stylesheet.

## 6. Design constraints

**What the canvas owns.** The chart (candles, axes, grid, crosshair, text on the chart, indicator lines, markers, pane layout) is drawn by the engine on a GPU canvas. CSS cannot restyle it. Chart colours, line weights, fonts and the like come from the engine and pack theme, and changing them is an engine/pack change, not a stylesheet change. How the designer's palette would be delivered to the engine (a theme object, a pack setting, or other) is **not yet defined**.

**What the designer can control:** everything around the canvas: top bar, title block, toolbar, legend and meta rows, rail and its panels, composer, task/evidence/activity cards, dialogs, notices and banners (including their placement over the chart), empty/loading/error states, badges and chips, buttons, form controls, responsive layout, focus styling, motion, copy and tone, and the colour tokens and type scale for all of that.

**Hard rules from the product:**
- Never imply live data when it is synthetic or delayed; data class and connection state are shown separately.
- A stale or retained frame must never read as current.
- Do not show a decorative substitute chart when rendering is unavailable.
- State must not rely on colour alone.
- Hiding assistant additions is presentation only and must say "Hidden in your view".
- There is no fallback renderer; the canvas is the only chart surface.
- A local crosshair drawn over the canvas (to make hover faster) is an open decision, so designs should not assume it.

**Accessibility (specified targets, not certified):** visible focus and logical focus order; accessible names on controls and the canvas (the canvas has a text description of keyboard use); polite announcements for task results and conflicts; touch targets at least 44 px; no horizontal page overflow on phone; reduced motion honoured; chart numbers and evidence available as text without reading pixels; Escape closes a view but never stops a task. A full screen-reader pass has not been recorded. Contrast ratios of the current palette have **not been audited**.

**Performance targets:** sources give targets for interaction rather than visual design: drag/pan preview within about 20 ms of the pointer moving; hover from browser-held data under about 50 ms (a goal, not today's behaviour); the chart should never blank on a transient error; indicator updates under about 5 s for a daily symbol; a long interaction session with zero "Rendering unavailable". A designer should expect that chart updates after a gesture may briefly lag the pointer, and design preview and "updating" states accordingly.

## 7. Planned (no dates, no promises)

- Faster interaction: live drag preview, batched wheel zoom, then browser-side crosshair and hover.
- Workspace releases: W1 (one assistant, one saved workspace; in development), W2 (invited people, shared and private conversation, independent or followed views, expiring phone pairing, shared edits and undo), W3 (multiple named assistants, independent analysis of a fixed snapshot, peer review).
- Indicators: fixed 0 to 100 scale and 30/70 reference lines for RSI; adjustable pane heights; intraday indicators; higher series limits.
- Data: dividend and earnings markers pending a source decision; breadth, relative strength, news and options are out of the current scope.
- A packaged visual design for the app itself is not claimed anywhere yet; this engagement may define it.

## 8. Open questions for the designer

1. A token system (colour, type, space, radius, elevation, motion) for the surrounding UI that can also be handed to the engine/pack as a chart theme. What is the cleanest split and format?
2. Light theme and dark theme as equals, including chart colours that remain distinguishable for colour-blind users and for up/down candle and indicator pairs.
3. Chart-state design: how should "updating", "reconnecting", "dimmed last frame", "failed" and "preview during drag" look so a retained picture is never mistaken for current?
4. Information density: very small labels (7 to 10 px) are common today. What is the right type scale for a dense analytical tool, and how does it hold up on phone?
5. The data-honesty vocabulary (synthetic, delayed, raw, split-adjusted, stored through a date, not stored): a consistent badge and message system.
6. The assistant presence: attribution of who made which change, fact versus interpretation versus limitation, and an evidence chip pattern that is clear about "as of then" versus "current".
7. Multi-person future: presence, shared versus personal view, and follow mode, without cluttering the single-user case.
8. Phone and tablet layouts: whether a switch between chart and conversation is right, and how the drawer should behave.
9. Branding: the current mark and name treatment are placeholders; a brand direction is **not yet defined**.

## 9. Feature parity with TradingView charting

How to read: **Have** = shipped, checked in the app code or demo. **Partial** = exists in a limited or development-only form. **Planned** = named in the team's roadmap or idea documents. **Not planned yet** = no source mentions it; this is the owner's intended gap list. TradingView's feature list comes from public knowledge, not from a live audit; rows marked (?) I am unsure of. "Foundation controls" means the controls in the Layers panel of the synthetic/development workspace; they were confirmed in code, not re-tested in the browser, and the live demo was not visually inspected for this section.

### Chart types
| Feature | Status | Design note |
|---|---|---|
| Candles | Have (engine draws OHLC candles on the price pane) | The only type the real-data chart shows. |
| OHLC bars | Partial (engine mark kind exists; no user switch) | Needs a chart-type switcher. |
| Line | Partial (engine mark kind exists; used for indicators, not as a price type switch) | Same switcher. |
| Area, Baseline, Columns, High-low | Not planned yet (a zero-based bar mark exists for volume) | Switcher plus per-type options. |
| Hollow candles, Volume candles | Not planned yet | |
| Heikin Ashi, Renko, Kagi, Line break, Point & Figure, Range | Not planned yet | These need derived data, which collides with the "no calculation" rule; a data-model decision comes first. |

### Timeframes and intervals
| Feature | Status | Design note |
|---|---|---|
| Daily | Have | |
| 1m and 5m | Partial (supported by the app's chart description; release scope is daily-first; intraday indicators are a follow-up) | Needs an interval picker; none exists. |
| Weekly, monthly, hours, custom intervals, seconds/ticks | Not planned yet | |

### Scales and panes
| Feature | Status | Design note |
|---|---|---|
| Log / linear axis | Partial (foundation controls only: "Use linear axis" / "Use log axis") | Should be a compact axis toggle on the chart. |
| Percent scale | Partial (per-layer shared / independent / percent in foundation controls; benchmark mode rebases to percent) | |
| Auto / lock scale, price-axis drag, time-axis drag | Not planned yet (?) | |
| Multiple panes | Have (indicator panes, cap of two) | Cap and message need a design. |
| Pane resize / merge / move | Not planned yet (pane heights are a named follow-up) | |
| Right/left axis, scale labels | Not planned yet | |

### Indicators and overlays
| Feature | Status | Design note |
|---|---|---|
| Stored presets: SMA, EMA, Bollinger, RSI, MACD, ATR | Have (real-data mode) | Preset picker; custom values are refused by design. |
| Volume bars | Partial (foundation control "Add volume bars") | Should be default-on pane. |
| Large indicator library (hundreds) | Not planned yet | Each one must be stored offline, so growth is gated by the utility. |
| VWAP, levels | Planned (intraday follow-up) | |
| Indicator settings dialog, style (colour/width) | Partial (edit-parameters picks stored presets only; styling not defined) | |
| Templates / saved sets | Not planned yet (session persistence of picks is planned) | |
| Pine Script / custom scripts | Not planned yet; conflicts with "no calculation" | |

### Drawing tools
| Group | Status | Design note |
|---|---|---|
| Trend line, horizontal line | Partial (development demo build only) | Anchors, handles, nudge buttons exist. |
| Rays, extended lines, vertical lines, channels | Not planned yet | |
| Fibonacci tools, Gann, pitchforks | Not planned yet | |
| Patterns (XABCD, head and shoulders, etc.) | Not planned yet | |
| Shapes (rectangle, ellipse, arrow, brush) | Not planned yet | |
| Text, notes, callouts | Partial (assistant adds evidence notes; no user text tool) | |
| Measure / ruler | Not planned yet | |
| Forecasting, position tools | Not planned yet (and sensitive given the no-advice stance) | |
| Volume-based (anchored VWAP, fixed range profile) | Not planned yet | |
| Magnet, lock, hide, object tree, style toolbar | Not planned yet | |

### Crosshair, legends, data window
| Feature | Status | Design note |
|---|---|---|
| Crosshair with values | Have (engine drawn, server rendered; slower than TradingView) | Local crosshair is an open owner decision. |
| Legend (symbol, OHLC, indicator values) | Partial (legend line and hover values; no full OHLC legend row) | |
| Data window panel | Not planned yet | |
| Hover tooltip with source and run | Have (indicator hover shows value and source) | |

### Navigation
| Feature | Status | Design note |
|---|---|---|
| Wheel zoom, drag pan, keyboard | Have | Drag currently jumps on release; live preview planned. |
| Live drag preview, batched zoom | Planned (smooth-interaction memo) | Needs a "preview" visual state. |
| Zoom to range, reset view, range buttons (1M, 6M, 1Y) | Not planned yet | |
| Bar replay | Partial (a synthetic recorded-stream replay mode exists; not a TradingView-style replay of history) | |
| Go to date, scroll to latest | Not planned yet (?) | |

### Compare and overlay
| Feature | Status | Design note |
|---|---|---|
| Benchmark comparison (SPY, QQQ, sector ETF) | Have (percent-rebased, up to four) | |
| Compare any symbol, overlay same scale, add as new axis | Not planned yet | |
| Multi-chart layouts and sync (crosshair, interval, symbol) | Not planned yet | Layout slots are a design question. |

### Alerts, watchlists, search
| Feature | Status | Design note |
|---|---|---|
| Alerts | Not planned yet | Needs a live-data model. |
| Watchlists, screener | Not planned yet | |
| Symbol search | Not planned yet (symbols are chosen from a fixed list in the demo) | Top-bar search is a likely first component. |

### Sessions and events
| Feature | Status | Design note |
|---|---|---|
| Extended hours / session breaks | Not planned yet (sessions are marked as New York time in data) | |
| Split, dividend, earnings markers | Have for splits (real-data mode); dividends and earnings Planned (source decision) | Marker key is colour-only today; add shape. |
| Price profile / volume profile | Not planned yet (explicitly out of the current release) | |

### Output, themes, settings
| Feature | Status | Design note |
|---|---|---|
| Snapshot / image export | Partial (PNG export in development demo build; not in the public demo) | |
| Share / publish chart link | Not planned yet (shared views belong to W2) | |
| Dark theme | Have | |
| Light theme, custom colours, chart settings dialog, background/grid options | Not planned yet | Depends on how the engine receives a theme. |
| Hotkeys | Partial (arrows, plus/minus, Escape; no shortcut list or others) | |
| Mobile / touch | Partial (phone layout, 44 px targets; touch gestures on the canvas not confirmed) | |
| Accessibility | Partial (see section 6) | Stronger than most charting tools on intent, unaudited in fact. |
| Data and trading panel, broker connection | Not planned yet; trading is out of scope for the product | |

### Biggest gaps, in suggested order
1. **Chart type switcher** and the common types (bars, line, area, hollow candles); it unlocks most visible parity and is mostly engine and pack work.
2. **Timeframe and range controls** (interval picker, 1M/6M/1Y buttons, reset view); none exist in the toolbar.
3. **Fast, local crosshair and a full OHLC legend**; the most visible "feels slower than TradingView" gap.
4. **Axis controls on the chart** (log, percent, auto, lock) and pane resize.
5. **Symbol search and any-symbol compare.**
6. **Theme system** (light, custom colours) and chart settings dialog.
7. **Drawing tools beyond trend and horizontal lines** (rays, Fibonacci, rectangles, text, measure) plus a drawing toolbar and object list.
8. **Volume as a default pane** and a larger indicator set, which depend on offline storage capacity.
9. Later: multi-chart layouts, alerts, watchlists, replay, extended hours, profiles. Non-price chart types (Renko, Kagi, Point and Figure) and scripts conflict with the "no calculation" rule and need an owner decision.

## Gaps in the source material

Not yet defined: chart types beyond OHLC, chart theme delivery to the engine, light theme, colour tokens, brand, contrast audit, tablet implementation, final drawing-tool scope, behaviour of shared-view collaboration screens, and any visual prototype or mock-ups for W2/W3.
