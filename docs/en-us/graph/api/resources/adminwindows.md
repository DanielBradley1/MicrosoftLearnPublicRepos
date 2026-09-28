<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/adminwindows?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# adminWindows resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a container for all Windows administrator functionalities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the device. Not nullable. Read-only. Returned by default. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| updates | [adminWindowsUpdates](https://learn.microsoft.com/en-us/graph/api/resources/adminwindowsupdates?view=graph-rest-beta) | Entity that acts as a container for all Windows Update for Business deployment service functionalities. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adminWindows",
  "id": "String (identifier)"
}
```
