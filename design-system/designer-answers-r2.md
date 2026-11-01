# Designer answers, round 2

Checked against the request list of 2026-11-01. Board numbers refer to the screens canvas.

## Blocks the next stories

**Default state, chart first (DC-15, DC-17).** Drawn as the default on every page with a chart. Folded panes are not rails any more. They are buttons at the left of the chart head (Menu, Chat), so the chart takes the full width and runs edge to edge.
- Boards: 64 (desktop), 64L (light), 64T and 64T-L (tablet 768), 9 and 33 (phone 390, dark and light), 64F (first visit).
- Chat button states: a count and "Approve" for a proposal waiting (64), a dot for a new message (65), and "Mat working" with a pulsing icon (67).
- First visit: one tip under the pane buttons, naming `[`, `]` and `o`. It is dismissed by "Got it" or by opening a pane, and never shown again.
- Opening: the menu floats over the chart and folds after a pick. Chat docks and pushes the chart on desktop.
- On demand: the legend, evidence, layers and data views, the less-used toolbar controls, and footer notices. The app footer is gone; its notice is the status line in the chart foot.

**Text under 12px (D7, DC-14).** Raised to 12px: count badges (`.cs-countbadge`, `.cs-iconbtn__count`), the avatar number (`.cs-avatar__num`), and `kbd.cs-kbd`.
Exempt, and the only exemptions:
- Initials inside avatars (`.cs-avatar` and its presence, author-chip and feed sizes, plus `.cs-avatar__via`).
- Marker letters (`.cs-marker`).
- Decorative glyphs that are `aria-hidden` and always sit next to a text label: `.cs-badge__glyph`, `.cs-chip__box`, `.cs-status__g`, `.cs-steps__g`, `.cs-pin__glyph`, `.cs-chg__g`, `.cs-sentto__g`, `.cs-warnchip::before`, and the unread dot.

A glyph is sized by its box, not the type scale. If it ever carries meaning on its own, it must be raised.

**Tablet (D9, DC-18).** Drawer. From 761 to 1023px, an open menu or chat is an opaque drawer over the chart, and the chart never resizes. One drawer is open at a time, and pane buttons are icon-only. Boards 11 and 63 now show the chat drawer open; 64T and 64T-L show the folded default.

**Add-agent limits (D8, AA-13 to AA-17).** Boards 59 to 62 show:
- Spend per task in USD, with the owner's ceiling.
- Spend per day in USD, with the owner's ceiling.
- Requests per minute, with the owner's ceiling.
- Output tokens per task (default 4,096, most 16,000).

We do not want an input-token limit or a tasks-per-day count. The USD limits already bound cost, requests per minute bounds bursts, and two more numbers would only confuse.

Tools are the contract's three flags: read, evidence, propose. The over-limit notice on board 58 speaks in USD and requests.

**Consent wording (D10, AA-14).** Board 57 has a "Wording for any provider" frame:
- Sent-to line: `Sent to <Provider>`.
- Dialog title: `Send this chart's data to <Provider>?`
- Buttons: `Not now` and `Allow for this workspace`.
- Provider line: `<Product> · <Model>`.

`<Provider>` is the company that receives the data (Anthropic, OpenAI). Local models say "Stays on this machine" and never ask for consent.

**Chart options on demand (0b).** Boards 64 to 69:
- (a) Always visible: the chart head (symbol, price, change, interval, warnings, one-line legend, Options handle) and the chart foot (data-class badge, status line, render stamp).
- (b) The toolbar fades in over the top of the chart when the pointer reaches the top edge, and the chart does not move (65). On touch, tap the Options button (69).
- (c) Right-click, Shift+F10 or the Menu key opens a context menu at the cursor: indicators, compare, draw here, copy price, reset view, settings (67).
  - **Pushback:** long-press stays the press-and-hold crosshair (boards 28 and 49), so touch gets the options from the Options button, not long-press. Two meanings for one gesture would break the read-out.
- (d) The legend is one line in the head and expands on hover or focus; Esc closes it (68).
- (e) A stale, delayed or partial warning is a chip in the head and tints the foot. It never hides behind a gesture (68).
- (f) `o` opens the options with focus on the first control, and the focus ring shows (66). Esc closes and returns focus to the chart. Every hover reveal has a tap and a key.
- (g) Phone rows and the Options button are 44px (69).

## Needed soon

- **Agent errors (D11).** Board 58 maps every code to one of three notice styles (refusal, caution, quiet) in six groups, with a fallback for unknown codes. The code itself appears only in small text for support.
- **Chart canvas: Follow theme (D12).** Board 25 shows the option disabled, with "The chart stays dark in light mode for now. Following the theme comes in a later release."
- **Light and 375 (D13).** Light versions of 49 to 58, 60 and 61 are drawn (suffix L). Widths we guarantee: 320 to 1920. Phone boards are drawn at 390 and the same rules hold at 375 and 320; nothing below 320.
- **Render stamp time zone.** UTC, as the app does. Provenance times (render stamp, data run, evidence inputs) are always UTC and say so. Conversation times may use the viewer's zone later, but must show the zone.
- **Narrow footer.** There is no app footer now. The chart foot wraps to as many lines as it needs at 375 and 320 and never truncates a warning (board 9).

## Small questions

- **Marker chip with no date.** The slot names the kind: "Range" for a span, "Level" for a horizontal line, "Note" for a free note. It is never blank.
- **Legend swatch colour.** The swatch uses the same resolved hex the engine was given for that layer (`series[i]` of the active theme object), not a CSS variable. While the canvas stays dark in light mode, the swatch uses the dark object's value, so it always matches the line.
- **Status lines.** `.cs-statusline` in the chart foot: one short sentence, sentence case, 12px, `role="status"`. It clears after 8 seconds unless it is a warning, which stays. Say what happened and why, for example "Undo isn't available: nothing to undo", not "Command unavailable: undo".
- **Top bar title font.** Not intended. Since round 2 only pane titles use the display font. The top bar title, the symbol and every number use IBM Plex Sans.
- **Run id.** One line, ellipsis at the end, the full id in a tooltip, and a copy button on hover or focus (`.cs-runid`). Never wrap.
