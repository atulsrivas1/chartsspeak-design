# Composer

The message box at the bottom of the rail, which states the assignment rule in words.

**Consumer provides:** a labelled `cs-textarea`, the send button and the hint line; mention highlighting is `cs-mention`.

- Only an explicit `@Mat` mention, or a reply to the assistant, starts a task, and the hint says so. Ordinary chat never silently becomes work.
- In the public demo the composer is replaced by one line: "Messaging is off in the read-only demo." Do not show a disabled box.
- Enter sends and Shift+Enter adds a new line. Escape leaves the composer and never stops a task.
