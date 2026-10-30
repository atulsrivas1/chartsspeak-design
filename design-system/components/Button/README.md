# Button

Primary, default and quiet buttons, at least `size-target` (44px) tall; `cs-btn--compact` (32px) is for desktop toolbars only.

**Consumer provides:** a `<button class="cs-btn">` with a verb-first label in sentence case, plus a modifier `cs-btn--primary`, `cs-btn--quiet`, `cs-btn--compact` or `cs-btn--icon`. An icon-only button needs an `aria-label`.

- Use one `--primary` per region, for the next action: "Ask Mat", "Sign in", "Retry".
- The Undo and Redo labels name what they reverse ("Undo add SMA 50"). When another edit has intervened, disable the button and show the reason in a caption instead of guessing.
- `--quiet` is for Cancel, Close and secondary rail actions.
- A disabled button always comes with a visible reason nearby. Do not disable a button silently.
