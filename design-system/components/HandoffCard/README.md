# HandoffCard

One agent passes an unfinished task to another, for example when its person goes offline. The card lists exactly what travels and what stays behind, and waits for the receiving agent's person to accept.

**Consumer provides:** the task, the sending and receiving agents with their people, the `PinnedSnapshot`, the two lists, and the actions.

- **Travels:** the question in the person's words, the pin, evidence produced so far, steps done and steps left, open questions.
- **Stays behind:** private conversation, the sender's personal view (zoom, hidden items), and the sender's grants. The receiver works only inside its own grants, and the card says what that changes ("Grace can propose, not apply").
- Only the receiving person can accept. Until then the task shows "Handoff pending" and nothing runs. Declining returns it to the sender, paused.
- Everything the receiver adds is attributed to the receiver, with "continued from Mat" in its result.
