<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamSummary resource type

Contains information about a team in Microsoft Teams, including number of owners, members, and guests.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| guestsCount | Int32 | Count of guests in a team. |
| membersCount | Int32 | Count of members in a team. |
| ownersCount | Int32 | Count of owners in a team. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "guestsCount": "Integer",
    "membersCount": "Integer",
    "ownersCount": "Integer",
}
```
