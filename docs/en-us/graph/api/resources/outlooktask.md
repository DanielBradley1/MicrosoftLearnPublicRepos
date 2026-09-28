<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-24 -->

# outlookTask resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Outlook tasks API is deprecated and stopped returning data on August 20, 2022. Use the [To Do API](https://learn.microsoft.com/en-us/graph/api/resources/todo-overview) instead.

An Outlook item that can track a work item.

You can use a task to track:

- The start, due, and actual completion dates and times.
- The progress or status of the task.
- The recurrence and reminder statuses of the task.

Date-related properties in the **outlookTask** resource include the following:

- completedDateTime
- createdDateTime
- dueDateTime
- lastModifiedDateTime
- reminderDateTime
- startDateTime

By default, the POST, GET, PATCH, and [complete](https://learn.microsoft.com/en-us/graph/api/outlooktask-complete?view=graph-rest-beta) operations return date-related properties in their REST responses in UTC. You can use the `Prefer: outlook.timezone` header to have all the date-related properties in the response represented in a time zone different than UTC. The following example returns date-related properties in EST in the corresponding response:

```
Prefer: outlook.timezone="Eastern Standard Time"
```

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/outlooktask-get?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) | Get the properties and relationships of an Outlook task in the user's mailbox. |
| [Update](https://learn.microsoft.com/en-us/graph/api/outlooktask-update?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) | Change writeable properties of an Outlook task. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/outlooktask-delete?view=graph-rest-beta) | None | Delete the specified task in the user's mailbox. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/outlooktask-permanentdelete?view=graph-rest-beta) | None | Permanently delete an Outlook task and place it in the Purges folder in the Recoverable Items folder in the user's mailbox. |
| [Complete](https://learn.microsoft.com/en-us/graph/api/outlooktask-complete?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) collection | Complete an Outlook task that sets the **completedDateTime** property to the current date, and **status** property to `completed`. |
| **Attachments** |  |  |
| [List attachments](https://learn.microsoft.com/en-us/graph/api/outlooktask-list-attachments?view=graph-rest-beta) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-beta) collection | Get all attachments on an Outlook task. |
| [Add attachment](https://learn.microsoft.com/en-us/graph/api/outlooktask-post-attachments?view=graph-rest-beta) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-beta) | Add a file, item \(message, event or contact\), or link to a file as an attachment to a task. |
| **Extended properties** |  |  |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) | Create one or more single-value extended properties in a new or existing Outlook task. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) | Get Outlook tasks that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) | Create one or more multi-value extended properties in a new or existing Outlook task. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-beta) | [outlookTask](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask?view=graph-rest-beta) | Get an Outlook task that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | The name of the person who has been assigned the task in Outlook. Read-only. |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | The task body that typically contains information about the task. Only the HTML type is supported. |
| categories | String collection | The categories associated with the task. Each category corresponds to the **displayName** property of an [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-beta) that the user has defined. |
| changeKey | String | The version of the task. |
| completedDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-beta) | The date in the specified time zone that the task was finished. |
| createdDateTime | DateTimeOffset | The date and time when the task was created. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| dueDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-beta) | The date in the specified time zone that the task is to be finished. |
| hasAttachments | Boolean | Set to true if the task has attachments. |
| id | String | Unique identifier for the task. By default, this value changes when the item is moved from one container \(such as a folder or calendar\) to another. To change this behavior, use the `Prefer: IdType="ImmutableId"` header. See [Get immutable identifiers for Outlook resources](https://learn.microsoft.com/en-us/graph/outlook-immutable-id) for more information. Read-only. |
| importance | importance | The importance of the event. The possible values are: `low`, `normal`, `high`. |
| isReminderOn | Boolean | Set to true if an alert is set to remind the user of the task. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the task was last modified. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| owner | String | The name of the person who created the task. |
| parentFolderId | String | The unique identifier for the task's parent folder. |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-beta) | The recurrence pattern for the task. |
| reminderDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-beta) | The date and time for a reminder alert of the task to occur. |
| sensitivity | sensitivity | Indicates the level of privacy for the task. The possible values are: `normal`, `personal`, `private`, `confidential`. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-beta) | The date in the specified time zone when the task is to begin. |
| status | taskStatus | Indicates the state or progress of the task. The possible values are: `notStarted`, `inProgress`, `completed`, `waitingOnOthers`, `deferred`. |
| subject | String | A brief description or title of the task. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attachments | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-beta) collection | The collection of [fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-beta), [itemAttachment](https://learn.microsoft.com/en-us/graph/api/resources/itemattachment?view=graph-rest-beta), and [referenceAttachment](https://learn.microsoft.com/en-us/graph/api/resources/referenceattachment?view=graph-rest-beta) attachments for the task. Read-only. Nullable. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-beta) collection | The collection of multi-value extended properties defined for the task. Read-only. Nullable. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-beta) collection | The collection of single-value extended properties defined for the task. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignedTo": "String",
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "categories": ["String"],
  "changeKey": "String",
  "completedDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "createdDateTime": "String (timestamp)",
  "dueDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "hasAttachments": true,
  "id": "String (identifier)",
  "importance": "string",
  "isReminderOn": true,
  "lastModifiedDateTime": "String (timestamp)",
  "owner": "String",
  "parentFolderId": "String",
  "recurrence": {"@odata.type": "microsoft.graph.patternedRecurrence"},
  "reminderDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "sensitivity": "string",
  "startDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "status": "string",
  "subject": "String"
}
```
