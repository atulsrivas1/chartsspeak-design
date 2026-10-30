# ShortcutSheet

All keyboard shortcuts in one dialog, opened with `?` or from Settings.

**Consumer provides:** a `Dialog` with a `cs-keys` grid: group headers and `cs-keys__row`s (action, then `kbd.cs-kbd` keys). Show ⌘ on Mac and Ctrl elsewhere.

- Single-letter shortcuts never fire while focus is in a text field, and can be turned off in Settings (WCAG 2.1.4).
- Escape closes the top view only. It never stops a task or discards an edit.
