# Field

Labelled select, text input and checkbox row, all 44px tall on `surface-000` with a `border-control` edge.

**Consumer provides:** a `cs-field` label wrapping `cs-field__label`, the control (`cs-input` or `cs-select`) and an optional `cs-field__hint`; checkbox rows are `<label class="cs-check">`.

- Every control has a visible label. Placeholder text is never the label.
- Hints state caps and consequences in `caption` size, which is never below 11px.
- Selects list stored options only. When something is missing, say how to get it ("Not stored. Request via utility") instead of listing it disabled.
