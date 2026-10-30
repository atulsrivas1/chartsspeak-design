# SettingsPage

Account and workspace settings: profile, appearance (theme with System, candle colours), data defaults (split-adjusted vs raw, default range), notifications (quiet mode, digest), shortcuts and paired phones.

**Consumer provides:** a `cs-settings` grid with a `cs-settings__nav` (one `aria-current` link) and sections of `cs-setting` rows (name, hint, control). Changes save on change and confirm in `StatusFooter` ("Theme set to System").

- Everything here is personal and never changes another person's view. Data defaults only apply to charts you open next.
- System theme follows `prefers-color-scheme` live. The engine receives the matching theme object at the same moment the CSS switches.
- A raw or adjusted default that isn't stored for a symbol falls back to what is stored, with the `DataClassBadge` saying so.
