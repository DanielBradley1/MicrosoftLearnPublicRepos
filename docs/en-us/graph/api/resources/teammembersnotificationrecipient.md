<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teammembersnotificationrecipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamMembersNotificationRecipient resource type

Namespace: microsoft.graph

Represents the recipient of a notification sent in a Microsoft Teams activity feed. The recipient consists of the team members.

Inherits from [teamworkNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teamworknotificationrecipient?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| teamId | String | The unique identifier for the team whose members should receive the notification. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamMembersNotificationRecipient",
  "teamId": "String"
}
```
