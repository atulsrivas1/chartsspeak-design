# ConversationScope

Shared and private conversation (W2). A switch at the top of the Conversation tab chooses where you are writing, and every message carries its scope.

**Consumer provides:** a `cs-tabs--switch` with Shared/Private, and on each message a `cs-scope--shared` or `cs-scope--private` label in the attribution line; private messages get `cs-msg--private` (dashed edge).

- The composer hint names the scope ("Writing to everyone" / "Only you see this").
- A private message can still start an assistant task. The result stays private until you share it with one action.
- In the single-person case the switch is hidden and every message is private.
