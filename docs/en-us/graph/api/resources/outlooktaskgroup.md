<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskgroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# outlookTaskGroup resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Outlook tasks API is deprecated and stopped returning data on August 20, 2022. Use the [To Do API](https://learn.microsoft.com/en-us/graph/api/resources/todo-overview) instead.

A group of folders \([outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta)\) that contain Outlook tasks \(collection of [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) objects\).

In Outlook, there's a default task group `My Tasks` which you can't rename or delete. You can, however, create additional task groups.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/outlooktaskgroup-get?view=graph-rest-beta) | [outlookTaskGroup](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskgroup?view=graph-rest-beta) | Get the properties and relationships of the specified Outlook task group. |
| [Update](https://learn.microsoft.com/en-us/graph/api/outlooktaskgroup-update?view=graph-rest-beta) | [outlookTaskGroup](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskgroup?view=graph-rest-beta) | Update the writable properties of an Outlook task group. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/outlooktaskgroup-delete?view=graph-rest-beta) | None | Delete the specified Outlook task group. |
| [List task folders](https://learn.microsoft.com/en-us/graph/api/outlooktaskgroup-list-taskfolders?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) collection | Get a collection of Outlook task folders. |
| [Create task folder](https://learn.microsoft.com/en-us/graph/api/outlooktaskgroup-post-taskfolders?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) | Create an Outlook task folder. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeKey | String | The version of the task group. |
| groupKey | Edm.Guid | The unique GUID identifier for the task group. |
| id | String | The unique string identifier of the task group. Read-only. |
| isDefaultGroup | Boolean | True if the task group is the default task group. |
| name | String | The name of the task group. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| taskFolders | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) collection | The collection of task folders in the task group. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "changeKey": "String",
  "groupKey": "Guid",
  "id": "String (identifier)",
  "isDefaultGroup": true,
  "name": "String"
}
```
