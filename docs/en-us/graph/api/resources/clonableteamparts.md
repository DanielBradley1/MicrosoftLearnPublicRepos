<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/clonableteamparts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-19 -->

# clonableTeamParts enum type

Namespace: microsoft.graph

Describes which part of a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) should be cloned.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| apps | 1 | Copy the list of installed apps. |
| tabs | 2 | copies the tabs within channels. |
| settings | 4 | Copies all settings within the team, along with key group settings. |
| channels | 8 | copies the channel structure \(but not the messages in the channel\). |
| members | 16 | copies the members and owners of the team. |
