# ResultCard

A completed assistant answer, always in three labelled parts: Calculated fact, Interpretation, Limitations.

**Consumer provides:** a `cs-card` with a completed `cs-task__state`, an `AttributionChip`, and up to three `cs-result__part` blocks in that order; footer actions (Open evidence, named Undo).

- Never merge the parts. Leave out an empty part rather than writing "None".
- Facts carry numbers; interpretation carries no numbers that the fact does not also state.
- Limitations always repeat the data class and coverage the fact was computed on.
