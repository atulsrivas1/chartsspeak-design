# CommandCopy

The copyable instruction pattern for anything only the data utility can do: one line of code with a Copy button.

**Consumer provides:** a `cs-cmd` with a `cs-cmd__prompt` "$", the command in `<code>`, and a Copy button; after copying, the button reads "Copied" for 2 seconds and the `StatusFooter` announces it.

- Use it wherever the honest answer is "this isn't stored": first run, symbol with no data, `RefusalNotice` bodies, `IndicatorPicker` rows.
- The command is real and complete. Never show a placeholder such as `<symbol>`; fill in the symbol the person asked for.
- The command shown here is an illustration. Use the real utility syntax.
