# Engine theme hand-off

This answers the overview's open question 1: how one token system serves both the CSS interface and the GPU canvas.

## The split

- **`tokens.json` is the only source.** Interface tokens (surfaces, ink, accent, states, type, spacing) are compiled to CSS custom properties and used only by the interface around the canvas.
- **Every `chart-*` colour token, plus the line, font and marker values below, is compiled into one theme object per theme** and passed to the engine. The engine never reads CSS, never parses `var()`, and never hard-codes a colour.
- **Delivery:** the SDK/viewer passes the object at mount and again on every theme or candle-colour change: `viewer.setTheme(theme)`. The pack does not own visual values. It declares *what* exists (series, events) and the theme says *how* it looks. This keeps a source adapter from ever changing appearance.
- **Generation:** a build step reads `tokens.json`, resolves each `chart-*` value for the requested theme, and emits the object below. Nobody edits the object by hand. A colour change on the design system page reaches the engine at the next build.

## The theme object (v1)

Colours are resolved hex/rgba strings; lengths are CSS px at 1× (the engine multiplies by the device pixel ratio).

```json
{
  "version": 1,
  "id": "dark",
  "candleMode": "blue-orange",
  "background": "#0b0f15",
  "grid": {
    "color": "#19212b",
    "width": 1,
    "lines": "horizontal"
  },
  "axis": {
    "text": "#a8b3c1",
    "font": "500 12px \"IBM Plex Sans\", system-ui, sans-serif",
    "tickLength": 4
  },
  "crosshair": {
    "color": "#c5ced4",
    "width": 1,
    "dash": [
      3,
      3
    ],
    "tagFill": "#c5ced4",
    "tagText": "#0b0f15"
  },
  "candle": {
    "up": {
      "stroke": "#56b4e9",
      "fill": "background",
      "wickWidth": 1,
      "bodyStroke": 1.2
    },
    "down": {
      "stroke": "#e69f00",
      "fill": "#e69f00",
      "wickWidth": 1
    }
  },
  "series": [
    "#e7ebf1",
    "#cc79a7",
    "#f0e442",
    "#009e73",
    "#8a97a6"
  ],
  "seriesWidth": 1.5,
  "benchmark": {
    "order": [
      4,
      1,
      2,
      3
    ],
    "dash": [
      6,
      4
    ],
    "width": 1.5
  },
  "events": {
    "split": {
      "color": "#9aa6ae",
      "glyph": "S"
    },
    "dividend": {
      "color": "#6bd4a8",
      "glyph": "D"
    },
    "earnings": {
      "color": "#f2a07b",
      "glyph": "E"
    },
    "marker": {
      "size": 18,
      "radius": 4,
      "glyphColor": "background",
      "font": "600 12px \"IBM Plex Sans\", system-ui, sans-serif"
    }
  },
  "selection": {
    "color": "#8fa6ff",
    "width": 1.5,
    "dash": [
      4,
      3
    ]
  },
  "drawing": {
    "color": "#a351f6"
  },
  "anchor": {
    "color": "#e7ebf1",
    "radius": 5,
    "hitRadius": 22
  },
  "reference": {
    "color": "#303940",
    "dash": [
      2,
      3
    ],
    "width": 1
  }
}
```

The light object (same shape, resolved from the same tokens) is what a person in light mode gets. The canvas follows the theme from Release 2; Release 1 passes the dark object in both modes.

```json
{
  "version": 1,
  "id": "light",
  "candleMode": "blue-orange",
  "background": "#ffffff",
  "grid": {
    "color": "#e8ecf1",
    "width": 1,
    "lines": "horizontal"
  },
  "axis": {
    "text": "#566170",
    "font": "500 12px \"IBM Plex Sans\", system-ui, sans-serif",
    "tickLength": 4
  },
  "crosshair": {
    "color": "#3a444c",
    "width": 1,
    "dash": [
      3,
      3
    ],
    "tagFill": "#3a444c",
    "tagText": "#ffffff"
  },
  "candle": {
    "up": {
      "stroke": "#0072b2",
      "fill": "background",
      "wickWidth": 1,
      "bodyStroke": 1.2
    },
    "down": {
      "stroke": "#d55e00",
      "fill": "#d55e00",
      "wickWidth": 1
    }
  },
  "series": [
    "#12171f",
    "#a8507f",
    "#7a6f00",
    "#007a59",
    "#66727f"
  ],
  "seriesWidth": 1.5,
  "benchmark": {
    "order": [
      4,
      1,
      2,
      3
    ],
    "dash": [
      6,
      4
    ],
    "width": 1.5
  },
  "events": {
    "split": {
      "color": "#6b7780",
      "glyph": "S"
    },
    "dividend": {
      "color": "#1a7a4c",
      "glyph": "D"
    },
    "earnings": {
      "color": "#a2402a",
      "glyph": "E"
    },
    "marker": {
      "size": 18,
      "radius": 4,
      "glyphColor": "background",
      "font": "600 12px \"IBM Plex Sans\", system-ui, sans-serif"
    }
  },
  "selection": {
    "color": "#3452d6",
    "width": 1.5,
    "dash": [
      4,
      3
    ]
  },
  "drawing": {
    "color": "#850aff"
  },
  "anchor": {
    "color": "#12171f",
    "radius": 5,
    "hitRadius": 22
  },
  "reference": {
    "color": "#c9d0d8",
    "dash": [
      2,
      3
    ],
    "width": 1
  }
}
```

Rules the engine must keep:

- `candle.up.fill: "background"` means up candles are **hollow**. `candleMode: "green-red"` swaps the two stroke/fill colours for `chart-up-conventional` and `chart-down-conventional`, and nothing else: up stays hollow, down stays filled.
- `series` is consumed in order. Benchmarks reuse `series[benchmark.order[i]]` **dashed**, so a benchmark never looks like an indicator.
- Event markers always draw their glyph, because colour alone is not enough.
- `reference` covers fixed guide lines such as RSI 30/70; it is quieter than the grid's meaning, not louder.
- `anchor.hitRadius` 22 gives the 44px touch target the interface promises.

## Versioning

Bump `version` whenever a field is added or its meaning changes. The engine refuses an unknown major version and keeps its last good theme (no blank frame), the same "never imply what isn't true" rule as everywhere else.
