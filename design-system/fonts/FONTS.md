# Fonts: the design's files and licences

These seven files are the design's type. The boards load the same families from Google Fonts only for previewing; the app must not. Host these files from the app's own origin and load `fonts.css`.

| Family | Weights | Used for | Licence |
|---|---|---|---|
| IBM Plex Sans | 400, 500, 600 | All interface text | SIL Open Font License 1.1 |
| IBM Plex Mono | 400, 500 | Prices, numbers, code, shortcuts | SIL Open Font License 1.1 |
| Bricolage Grotesque | 600, 700 | Wordmark, page and pane titles, the symbol | SIL Open Font License 1.1 |

- **Subset:** Latin (Basic Latin, Latin-1, general punctuation, currency, arrows used in the interface). Add the Latin Extended files from the same source if a language needs them.
- **Format:** woff2 only. Every browser the app supports reads it.
- **Self-hosting is allowed.** The OFL permits bundling, embedding and redistributing the files with an app, free of charge, as long as the licence text travels with them. The three `LICENSE-*.txt` files in this folder do that; ship them in the app's licences screen or build output. The fonts may not be sold on their own, and a modified font may not keep the reserved name.
- **Source:** the files are the unmodified Latin woff2 builds from the Fontsource packages (version 5.3.0) of the upstream fonts, so they match what Google Fonts serves.
- **Fallbacks:** `IBM Plex Sans`, then `system-ui`, then `sans-serif`; mono falls back to `ui-monospace`; the display face falls back to the sans stack. The chart canvas uses the Plex Sans file too (see engine-theme.md), loaded before the first frame so axis labels do not change width.
- **Weights not used:** italics, 300 and 700 of Plex Sans, 600 and 700 of Plex Mono. Do not ship them.
