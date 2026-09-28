<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-assignedgroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# assignedGroup resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the update deployment audience defined as a Microsoft Entra group.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupId | String | The unique identifier for the group. Returned by default. Key. Not nullable. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) | Represents a Microsoft Entra group. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.assignedGroup",
  "groupId": "String"
}
```
