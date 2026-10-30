# SaveStateChip

The workspace save state in the title block: Saved, Saving, Needs attention or Local.

**Consumer provides:** a `cs-badge` with the state's modifier (`--good` for Saved, `--caution` for Needs attention, none otherwise), a glyph and the word.

- Needs attention links to the `StatusFooter` retry/resolve controls. It does not open a dialog.
- Saving shows no spinner; the word is enough.
