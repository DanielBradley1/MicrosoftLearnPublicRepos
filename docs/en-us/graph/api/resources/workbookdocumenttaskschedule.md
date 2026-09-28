<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttaskschedule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# workbookDocumentTaskSchedule resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the start and due time of a [workbookDocumentTask](https://learn.microsoft.com/en-us/graph/api/resources/workbookdocumenttask?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dueDateTime | DateTimeOffset | The due date and time for the task. Nullable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| startDateTime | DateTimeOffset | The start date and time for the task. Nullable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workbookDocumentTaskSchedule",
  "dueDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)"
}
```
