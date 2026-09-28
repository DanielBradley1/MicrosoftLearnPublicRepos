<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-24 -->

# outlookTaskFolder resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Outlook tasks API is deprecated and stopped returning data on August 20, 2022. Use the [To Do API](https://learn.microsoft.com/en-us/graph/api/resources/todo-overview) instead.

A folder that contains Outlook tasks \(collection of [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) objects\).

In Outlook, the default task group, `My Tasks`, contains a default task folder, `Tasks`, for the user's mailbox. You can't rename or delete these default task groups or folders, but you can create new task groups and folders.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/outlooktaskfolder-get?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) | Get the properties and relationships of the specified Outlook task folder. |
| [Create task folder in group](https://learn.microsoft.com/en-us/graph/api/outlooktaskfolder-post-tasks?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) | Create an Outlook task in the specified task folder. |
| [List task folders in group](https://learn.microsoft.com/en-us/graph/api/outlooktaskfolder-list-tasks?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) collection | Get all the Outlook tasks in the specified folder. |
| [Update](https://learn.microsoft.com/en-us/graph/api/outlooktaskfolder-update?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) | Update the writable properties of an Outlook task folder. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/outlooktaskfolder-delete?view=graph-rest-beta) | None | Delete the specified Outlook task folder. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/outlooktask-permanentdelete?view=graph-rest-beta) | None | Permanently delete an Outlook task and place it in the Purges folder in the Recoverable Items folder in the user's mailbox. |
| **Extended properties** |  |  |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) | Create one or more single-value extended properties in a new or existing Outlook task folder. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) | Get Outlook task folders that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) | Create one or more multi-value extended properties in a new or existing Outlook task folder. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-beta) | [outlookTaskFolder](https://learn.microsoft.com/en-us/graph/api/resources/outlooktaskfolder?view=graph-rest-beta) | Get an Outlook task folder that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeKey | String | The version of the task folder. |
| id | String | The identifier of the task folder, unique in the user's mailbox. Read-only. |
| isDefaultFolder | Boolean | True if the folder is the default task folder. |
| name | String | The name of the task folder. |
| parentGroupKey | Guid | The unique GUID identifier for the task folder's parent group. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-beta) collection | The collection of multi-value extended properties defined for the task folder. Read-only. Nullable. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-beta) collection | The collection of single-value extended properties defined for the task folder. Read-only. Nullable. |
| tasks | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) collection | The tasks in this task folder. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "changeKey": "String",
  "id": "String (identifier)",
  "isDefaultFolder": true,
  "name": "String",
  "parentGroupKey": "Guid"
}
```
