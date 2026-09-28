<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/aadusernotificationrecipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# aadUserNotificationRecipient resource type

Namespace: microsoft.graph

Represents a Microsoft Entra user recipient of a notification sent in a Microsoft Teams activity feed.

Inherits from [teamworkNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teamworknotificationrecipient?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userId | String | Microsoft Entra user identifier. Use the [List users](https://learn.microsoft.com/en-us/graph/api/user-list?view=graph-rest-1.0) method to get this ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.aadUserNotificationRecipient",
  "userId": "String"
}
```
