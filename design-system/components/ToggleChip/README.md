# ToggleChip

An on/off chip for stored presets (indicators, benchmarks, layers), with state carried by `aria-pressed`, a check box and a fill.

**Consumer provides:** `<button class="cs-chip" aria-pressed>` containing a `cs-chip__box` and the preset name; an optional `cs-chip__src` names where it draws ("pane", "overlay").

- Offer stored presets only. A custom period is never a chip: show the `RefusalNotice` "Not stored" instead.
- Caps are explained in words under the row ("2 of 2 indicator panes in use", "3 of 4 benchmarks"). Do not just disable the chip.
- Group chips with `role="group"` and an `aria-label`.
