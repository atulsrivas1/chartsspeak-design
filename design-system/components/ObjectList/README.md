# ObjectList

Everything drawn on the shared chart (indicators, drawings, assistant markers), each with who added it and when, a personal hide toggle and a lock. It lives in the Layers tab, and the "On this chart" strip is its short form.

**Consumer provides:** a `cs-objlist` of `cs-objrow` items: a swatch in the object's chart colour, name, `cs-objrow__by` attribution, and two icon buttons (hide in your view, lock) with `aria-pressed` and full `aria-label`s; `aria-selected` on the row selected on the canvas.

- Hide is personal view: the row stays and its attribution reads "Hidden in your view".
- Lock prevents edits by anyone, including the assistant. Removing an item is a separate, undoable action from the row's menu.
- Selecting a row highlights the object on the canvas with `chart-selection`.
