# ChartsSpeak design

Design system and screen designs for ChartsSpeak, the assistant-first chart workspace.

## What's here

| Folder | What it is |
|---|---|
| `design-system/` | The design system. Start with `design-system/README.md` (the brand book and usage rules). |
| `design-system/tokens.json` | The single source for every value: colour (dark and light), type, spacing, radius, shadow and size. |
| `design-system/tokens.css` | The tokens as CSS custom properties (`:root` / `[data-theme="dark"]` and `[data-theme="light"]`). |
| `design-system/components/bundle.css` | All component styles as framework-agnostic `cs-*` classes. Load it after `tokens.css`. |
| `design-system/components/<Name>/` | One folder per component: `README.md` (when and how to use it) and `preview.html` (a live example). |
| `design-system/engine-theme.md` | How the `chart-*` tokens are compiled into the theme object the GPU chart engine receives. |
| `screens/` | The screen designs: 43 app screens (dark, plus light versions of the main ones), the brand board and a shared chart stand-in, as `.dc.html` files plus `canvas.json` (layout). |
| `design-system/engineering-answers.md` | Answers to engineering's questions, plus the interface contrast audit. |
| `docs/designer-overview.md` | The original designer brief the work was built from. |

## Using it in the app

```html
<link rel="stylesheet" href="design-system/tokens.css">
<link rel="stylesheet" href="design-system/components/bundle.css">
<html data-theme="dark"> <!-- or "light" -->
```

Then use the markup in each component's `preview.html`. The components are plain HTML and CSS, so they work with React or anything else. The chart canvas is not styled by CSS: hand the engine the theme object described in `design-system/engine-theme.md`.

## Rules that matter most

- Never imply live data. Data class (Synthetic, Stored daily, Delayed) and connection state are separate, fixed vocabularies.
- A retained chart frame never reads as current: it's veiled, timestamped and labelled "Not current".
- Assistant answers are always split into Calculated fact, Interpretation and Limitations.
- Nothing smaller than 11px, every control at least 44px tall, and state is never shown by colour alone.
- The logo is the `cs-wordmark`: "ChartsSpeak" with the woven SS, always in two colours.

## Screens

`screens/*.dc.html` are design-canvas files. They load a runtime (`support.js`) that the design canvas provides, so they render inside the canvas rather than as standalone pages. `screens/ds/chartsspeak/` is the copy of the design system those screens use. The chart in every screen is a stand-in (`ChartFrame.dc.html`); the real chart is drawn by the engine.

## Round 2

Added in round 2, all in both themes:

- **Working together:** participant roster, author filter, stale-base and undo-refused notices, proposals, live agent work, invites, agent grants, phone pairing.
- **Getting started and empty states:** first-run checklist, empty states, coverage bar, copyable utility commands.
- **Sharing and settings:** export (the data stamp is always on), share links, activity feed, toasts, settings, shortcuts, touch gestures, indicator style.
- **Agents checking each other:** review requests, side-by-side disagreement, handoff cards and a pinned-snapshot badge.
- **Light theme** screens for the main working views, and the wordmark in every screen header.
- **Beyond one chart (owner go-ahead):** multi-chart layouts with sync and templates, a stored-data watchlist and alerts, and bar replay.
