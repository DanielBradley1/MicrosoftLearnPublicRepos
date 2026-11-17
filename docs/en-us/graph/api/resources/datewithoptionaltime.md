<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# dateWithOptionalTime resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a date value used by the **startDateTime**, **dueDateTime**, and **finishDateTime** properties of a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta).

When creating or updating a task, supply only **date**. The **time**, **timeZone**, and **isTimeSpecified** properties describe returned values and must not be sent in write requests.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| date | Date | The date component of the value. |
| isTimeSpecified | Boolean | Indicates whether a specific time \(not just a date\) was provided. Read-only. |
| time | TimeOfDay | The optional time-of-day component of the value. Read-only. |
| timeZone | String | Time zone the time value is expressed in, if time is set. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.dateWithOptionalTime",
  "date": "Date",
  "time": "String (time of day)",
  "timeZone": "String",
  "isTimeSpecified": "Boolean"
}
```
