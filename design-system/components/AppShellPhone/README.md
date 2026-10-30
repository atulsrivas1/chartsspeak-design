# AppShellPhone

Phone (≤760px): two screens, Chart and Conversation, with the switch at the bottom of the screen.

**Consumer provides:** `data-screen="chart|conversation"` on the shell, kept in sync with the switch.

- The chart panel runs edge to edge. The toolbar scrolls sideways and its controls go back to 44px.
- Switching screens keeps the chart's view and the draft message. When a task finishes while you are on the Chart screen, the result is announced in the footer, with a link to the conversation.
- The Escape and keyboard rules are the same as on desktop.
