# Product decisions, 1 Nov 2026

Seven decisions from the product and design review. Each lists what changes and the boards that show it.

## 1. Layers and Data belong to the chart
The chat pane keeps three views: Chat, Activity and Evidence.
- **Layers** move to the expanded legend. It opens on hover or focus, and a click pins it. Each row can show, hide or remove its layer, and "+ Indicator" sits at the bottom.
- **Data** moves to a panel that opens from the data badge in the chart foot. It holds coverage, adjustment, data run and the last bars, with Copy as CSV.

Boards 50 and 51 now show these panels. Board 68 is the hover form.

## 2. One home per action
- **Menu:** switch what you look at (charts, watchlist, alerts). The "On this chart" rows are gone.
- **Chart:** change what you see. The Options toolbar, the legend and the data badge are the homes; the context menu and phone sheet are the same toolbar.
- **Chat:** ask and approve.
- **Undo** stays in two places on purpose. The toolbar undoes your last edit; a task card undoes that agent's change.
- **Shortcuts:** the command palette (6) is the keyboard copy of all three, not a new home.

## 3. One way to ask anyone
- **Recipient chip:** the composer has a chip, **To: Mat ▾**, listing agents, people, and Everyone in this workspace. Plain messages go to the chip's recipient, and `@name` sets the chip. The chip remembers your last recipient per chart. With no agent, the default is Everyone.
- **The line under the composer** says where the message goes. For an agent: "Sent to Anthropic". For a person: "Notifies Atul · stays in this workspace". For Everyone: "Stays in this workspace".
- **Asking a person** makes the same request card as an agent: Asked, then Working, then Answered, and "Waiting for Atul · seen 2 min ago". A person acting as an assistant sends changes as proposals, into the same approvals list.

Board 72.

## 4. Fewer approvals, same safety
- **Grouped proposals:** one task makes one proposal. It's drawn dashed on the chart with a checklist: Apply all, or untick items.
- **Apply without asking:** per agent, and off by default. It covers only adding markers, highlights and indicators on charts private to you; a toast with Undo and an Activity line follow every auto-applied change. It is offered once, after three proposals from that agent were applied unchanged.
- **Always asks:** shared charts, anything that removes or changes existing work, alerts, and anything a person proposed.
- **Contract:** one proposal per task, plus a per-agent auto-apply flag.

Board 73.

## 5. Ask about a selection
- **Mouse:** Shift+drag selects a range (plain drag still pans), and an "Ask about this" button appears beside it.
- **Right-click:** a bar, marker or drawing gives "Ask about this…".
- **Touch:** the held read-out has an Ask button, and dragging its edge widens it into a range.
- **Keyboard:** Shift+arrows extend a range, and Enter asks.
- **Result:** chat opens with a selection chip in the composer, "NVDA · 14 Mar – 2 Apr (14 bars)". The range stays shaded, and the sent-to line says only the selected bars are sent.
- **Voice, next round:**
  - Push-to-talk by default.
  - Opt-in hands-free on an on-device wake word ("Hey Charts"). Nothing is sent before the wake word. The mic indicator is always visible, there's a one-key mute, and it switches itself off after an idle time.
  - Voice can ask, select and navigate, but changes to shared work, or any order, need a visible confirm.
  - Spoken announcements: Off (default), Important only, or Everything. Never prices on a timer. A screen reader's live region comes first.
  - A mic slot is reserved in the composer now.

Boards 74 and 75.

## 6. Command palette
- **Opens with** Ctrl+K (Cmd+K on Mac) or `/`.
- **Typing a ticker** puts charts first. A symbol that isn't stored shows "not stored" and why.
- **Typing an action** finds actions and settings, and each row shows its shortcut.
- **The last row** is always "Ask Mat: …", using the recipient chip.
- **On phone,** a search field at the top of the Menu tab opens it.
- **One action registry** feeds the toolbar, context menu, palette and, later, voice.

Board 76.

## 7. Since you were last here
- **One line** in the chart foot's status slot after anything changed. For example: "Since Fri 16:02: 1 new bar · 1 alert fired · 2 proposals waiting · Atul changed SMA 200".
- **Opening it** shows the list in chat's Activity view, and each line jumps to its place. It clears once opened or after your first action.
- **Built from the event log:** no AI, exact and free.
- **Opt-in later:** an agent-written brief after each data run, with calculated fact and interpretation kept apart and counted against the agent's USD limit.

Board 77.

## Added the same day
- **74K:** select a range with the keyboard. With the crosshair on a bar, Shift+arrows extend the range, Enter asks and Esc clears.
- **67:** the context menu now starts with "Ask about this bar…", showing who it goes to.
- **76P:** on phone, the palette is a search field at the top of the Menu tab.
- **78:** push-to-talk. Hold the mic button, or Space while the message box is empty. The words appear in the message box as you speak, and a line says where speech is processed.
- **79:** Settings, Voice.
  - Talk to ChartsSpeak: Off or Push-to-talk.
  - Hands-free: off by default.
  - Auto-off time.
  - Where speech is processed.
  - Announcements: Off, Important only, Everything.
  - Quiet hours.
  - "Changes by voice: always confirm."
- **80:** hands-free.
  - A mic indicator shows in the top bar, with a mute key (Ctrl+Shift+M).
  - A spoken change to shared work shows a confirm card ("Remove SMA 200 for everyone?"). It accepts "confirm"/"cancel" by voice, or Enter/Esc.
- **81:** the opt-in agent brief tops the "since you were last here" list. Calculated fact and interpretation are kept apart, with the cost and sent-to shown and a link to turn it off.
- **Phone boards:** menu and chat are never folded on phone; tabs replace folding.

## Owner decisions
1. **Candles: green/red by default.** Blue/orange (`chart-up-cvd` / `chart-down-cvd`) is one click away in Settings and is offered at first run with a preview. Up stays hollow and down stays filled, so direction never depends on colour. The interface's "good" colour moves to teal (`#5fd3c8` dark, `#0f766e` light), so it doesn't read as an up candle. Its colour difference from the up candle roughly doubled (ΔE about 20, against 11 before), including under deutan and protan vision.
2. **People:**
   - **Release 1:** presence only (online/away, and "seen" on requests), which the To chip and request cards need.
   - **Release 2:** the people row with follow.
   - **Team video:** dropped. "Start a call" opens the team's own call tool with a link to the chart.
3. **Chart canvas follows the theme in Release 1.1.** Release 1 ships with it disabled ("arrives in Release 1.1"). Image exports should use the canvas the person sees, or offer dark or light in the export dialog.
