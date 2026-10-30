# InviteDialog

Invite a person to a workspace with one role, chosen from three described options.

**Consumer provides:** a `Dialog` with an email `Field`, a `cs-choice` fieldset of radio options (name plus one-line description of what the role can do), an expiry note, and Cancel / Send invite.

- Proposed roles: **Viewer** (read and shared conversation), **Editor** (shared edits, ask agents, approve proposals on their own items) and **Owner** (adds invites, roles and agent grants). The final role set is the PO's call.
- Describe each role by what it can do, never by a level number.
- After sending, the person shows in `ParticipantRoster` as "Invited · expires in 7 days" until they accept.
