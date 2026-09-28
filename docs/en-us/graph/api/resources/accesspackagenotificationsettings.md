<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagenotificationsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# notificationSettings resource type

Namespace: microsoft.graph

Used for the **accessPackageNotificationSettings** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). Provides details on if access package assignment email notifications are disabled within the specified access package assignment policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isAssignmentNotificationDisabled | Boolean | Indicates if notification emails for an access package are disabled within an access package assignment policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageNotificationSettings",
  "isAssignmentNotificationDisabled": "Boolean"
}
```
