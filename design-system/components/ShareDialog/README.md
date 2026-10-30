# ShareDialog

Share a snapshot (frozen at a revision) or the live workspace, with a stated audience and expiry.

**Consumer provides:** a `Dialog` with a `cs-choice` (Snapshot as of now, or The live workspace), audience and expiry selects, a `cs-linkbox` with Copy link, and a note on what viewers can do.

- Snapshot is the default, because it can't drift from what you meant to show.
- An anyone-with-the-link audience is read-only, like the public demo, and always shows the data label.
- Expired links open a page that says "This link expired on <date>", and never a blank chart.
