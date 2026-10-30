# AuthorFilter

A row of author chips under the chart legend: who drew what, how many items each, and a personal toggle to hide one author's items.

**Consumer provides:** a `cs-authors` group of `cs-authorchip` buttons with `aria-pressed` (true means shown), the author's avatar, name and item count; when hidden, the count line reads "<n> · Hidden in your view".

- Hiding is personal view only. It never deletes anything or changes anyone else's chart.
- Hidden chips get a dashed edge and dimmed avatar, plus the words. Selecting an item on the canvas highlights its author's chip.
- The same counts appear in `ObjectList`. This row is the quick filter; the list is the detail.
