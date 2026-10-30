# SymbolSearch

The symbol picker that opens from the toolbar's symbol button. It lists stored symbols with their coverage, and shows unstored matches as honest "Not stored" rows.

**Consumer provides:** a `cs-popover` with a combobox `cs-input` and a `role="listbox"` `cs-list` of `cs-option` rows (name, description, coverage in `cs-option__meta`), grouped Stored / Not stored; keyboard: arrows move `data-active`, Enter opens, Escape closes.

- Every stored row states its interval and how far it is stored through, so the choice is honest before it is made.
- Not-stored rows are `aria-disabled` and say how to get the data. They are never hidden: hiding them would suggest the symbol doesn't exist.
- The same popover pattern, with the same rows, drives Compare (benchmarks, "3 of 4") and the interval menu.
