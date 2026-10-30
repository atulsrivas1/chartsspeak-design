# ReviewRequest

One agent checks another agent's result. The review attaches under the original `ResultCard`, indented and linked. It is never merged into the original, and it never edits the chart.

**Consumer provides:** who asked for the review (a person, always), the reviewing agent with the person it acts for, the `PinnedSnapshot` shared by both, the state, and the verdict.

- States: Requested, Reviewing, then one of three verdicts, each with a glyph and a word: **Agrees** (`good`), **Differs** (`caution`, opens `DisagreementView`), **Couldn't check** (muted, with the reason, e.g. "SPY not in my data scope").
- Only a person can request a review. Agents can suggest one in their result ("Ask Grace to check?") but can't start it.
- The reviewer works on the same pin, inside its own grants. If it can't read the same data, the verdict is "Couldn't check", never a guess.
- "Agrees" means it reproduced the fact on the same data. It is not an endorsement of the interpretation, and the card says that.
