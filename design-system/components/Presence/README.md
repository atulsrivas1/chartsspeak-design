# Presence

Who is in the workspace now (W2): an avatar stack in the `TopBar`, with a coloured ring per invited person and the assistant in its accent ring, and one line naming them.

**Consumer provides:** a `cs-presence` with `cs-avatar--lg` items (`--person` for you, `--p1…p3` rings for invited people, the assistant last) and an `aria-label` that names everyone.

- A presence colour always sits next to initials and a name. It is used for that person's cursor and follow banner only, never for their edits (`AttributionChip` names those).
- In the single-person case the stack is just your avatar. Nothing is added to the shell until someone is invited.
- Phone pairing shows as a tag with its expiry.
