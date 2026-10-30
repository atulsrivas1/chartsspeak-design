# TabBar

Rail tabs (Conversation, Evidence, Activity, Layers, Data) with an `accent` underline on the selected tab; the `cs-tabs--switch` variant is the two-button Chart / Conversation switch on phone.

**Consumer provides:** a `role="tablist"` container of `cs-tab` buttons with `role="tab"` and `aria-selected`, optional `cs-tab__count`; arrow-key movement between tabs.

- Order is fixed: Conversation, Evidence, Activity, Layers, Data. Development-build tabs (Drawings, State, Export) go after Data.
- On narrow rails the bar scrolls horizontally. Do not wrap it onto two lines.
- The phone switch keeps chart state when you switch to Conversation and back.
