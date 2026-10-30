# TitleBlock

The page heading: an eyebrow, the title in `title-page`, an optional state chip, and at most one descriptive line.

**Consumer provides:** the eyebrow (an uppercase `label`, set in CSS), the title, and the line.

- **Use it for pages, not workspaces:** Settings, Agent grants, first run, and phone screens. On desktop and tablet workspace screens the title moves into `TopBar`, so the chart gets the height.
- **Never repeat the data label here.** The data class, adjustment and "through" date live in the chart toolbar only. On phone, where the toolbar has no room for them, the line under the title is their one home.
- Facts that are about this view and appear nowhere else (a snapshot's "as of", a coverage gap) go in one `cs-pageline` above the chart.
- One title block per screen. On phone `title-page` drops to 21/26.
