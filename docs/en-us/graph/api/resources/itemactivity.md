<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-18 -->

# itemActivity resource type

Namespace: microsoft.graph

The **itemActivity** resource provides information about activities that took place on an item or within a container. Currently only available on SharePoint and OneDrive for Business.

The actions that took place within an itemActivity are detailed in the [itemActionSet](https://learn.microsoft.com/en-us/graph/api/resources/itemactionset?view=graph-rest-1.0#properties) property.

> **Note:** **itemActivity** is currently only available on SharePoint and OneDrive for Business.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List activities](https://learn.microsoft.com/en-us/graph/api/itemactivity-list?view=graph-rest-1.0) | [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) collection | List the recent [activities](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) that took place on a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), item, or within an item hierarchy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| access | [accessAction](https://learn.microsoft.com/en-us/graph/api/resources/accessaction?view=graph-rest-1.0) | An item was accessed. |
| activityDateTime | DateTimeOffset | Details about when the activity took place. Read-only. |
| actor | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of who performed the action. Read-only. |
| id | string | The unique identifier of the activity. Read-only. |

## Relationships

| Relationship name | Type | Description |
| :--- | :--- | :--- |
| driveItem | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Exposes the **driveItem** that was the target of this activity. |
| listItem | [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) | Exposes the **listItem** that was the target of this activity. |

## JSON representation

```json
{
  "id": "string (identifier)",
  "access": "microsoft.graph.accessAction",
  "actor": {"@odata.type": "microsoft.graph.identitySet"},
  "driveItem": {"@odata.type": "microsoft.graph.driveItem"},
  "listItem": {"@odata.type": "microsoft.graph.listItem"},
  "activityDateTime": {"@odata.type": "String (timestamp)"}
}
```
