# AlertEditor

Creates an alert on a stored daily close. The condition is built from three choices, so it can always be read back as one sentence, and the dialog states plainly when it is checked.

**Consumer provides:** symbol, the three-part condition (value, comparison, target), expiry, delivery, and the sentence summary.

- Values and targets come only from stored series and stored indicators; anything else appears disabled with "Not stored".
- "Checked after each daily update, about 21:00 ET. Not real-time: a move during the day counts only if the close confirms it." This line is fixed and always shown.
- The summary sentence under the condition is what the alert list will show, so the person sees exactly what they're creating.
- Expiry is required (1 week, 1 month, 3 months). Alerts without an end pile up and get ignored.
