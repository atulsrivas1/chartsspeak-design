# ExportDialog

Export the chart as an image whose stamp carries the data-honesty label: symbol and interval, data class and adjustment, an "as of" date, an optional evidence caption and the wordmark.

**Consumer provides:** a `Dialog` with a live `cs-export__preview` (the engine's frame plus the `cs-stamp` strip exactly as it will be exported), a format `Field`, and checkboxes. The data label and date checkbox is checked and disabled with "(always on)".

- The stamp can never be turned off. That is the product rule: "exports must carry the data-honesty label."
- Hidden items are left out by default ("Include my hidden items" is off), so an export matches what others see, not your personal view.
- The public demo shows Export disabled with "Read-only demo", not hidden, because signing in makes it available.
