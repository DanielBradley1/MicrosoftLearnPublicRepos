<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/taskviewpoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-22 -->

# taskViewpoint resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains personal properties of a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta). When sharing or assigning a **task**, these properties won't be seen by other users.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reminderDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-beta) | The date and time for a reminder alert of the **task** to occur. |
| categories | String collection | The categories associated with the task. Each category corresponds to the **displayName** property of an [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-beta) that the user has defined. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.taskViewpoint",
  "reminderDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "categories": ["string"]
}
```
