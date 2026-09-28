<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-excludedgroupassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# excludedGroupAssignment resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the update deployment audience with excluded groups. Groups are logical containers of devices represented by Microsoft Entra groups.

Inherits from [groupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-groupassignment?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignments | [microsoft.graph.windowsUpdates.assignedGroup](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-assignedgroup?view=graph-rest-beta) collection | A collection of entities that govern the update deployment audience, defined as a Microsoft Entra group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.excludedGroupAssignment",
  "assignments": [{"@odata.type": "microsoft.graph.windowsUpdates.assignedGroup"}]
}
```
