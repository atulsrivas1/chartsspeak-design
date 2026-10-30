# UndoRefused

Undo refuses when another edit touched the same item afterwards, and says which edit, by whom and when.

**Consumer provides:** the disabled Undo button (still naming its action) with `aria-describedby` pointing at a `--caution` `RefusalNotice`: "Can't undo yet." plus the intervening edit, and two ways forward.

- Never undo past someone else's edit silently, and never undo it without naming it.
- "Remove … instead" makes a new, forward edit, which is itself undoable.
