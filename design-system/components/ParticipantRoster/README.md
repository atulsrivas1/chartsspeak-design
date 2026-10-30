# ParticipantRoster

Who is in the workspace, people and agents together: a compact strip for the top bar and a full list for the rail's People tab.

**Consumer provides:** a `cs-rosterstrip` of avatars (with an `aria-label` that counts people and agents), and a `cs-roster` list grouped People / Agents. Each row has an avatar, name, role line (for agents: "Agent · <role> · for <person>") and a `cs-status`.

- **Person or agent is shown by shape, never colour.** People are circles (`cs-avatar--person`, `--p1…p4`); agents are squircles with the accent ring (`cs-avatar--agent`). An agent carries a small badge with the initials of the person it works for (`cs-avatar__via`).
- **Colour identifies people, up to four** (`presence-1…4`). From the fifth person on, the ring is neutral (`cs-avatar--overflow`) with a number badge (`cs-avatar__num`). Agents are told apart by name and initial, all in the same accent ring.
- **Status always has a glyph and a word:** ● Working/Active, ○ Idle, ! Waiting for approval (caution), ◌ Away (muted, italic).
- In the single-person case, the strip shows only you and Mat, and the People tab is hidden.
