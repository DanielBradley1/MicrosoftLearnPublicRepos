<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# workPlanRecurrence resource type

Namespace: microsoft.graph

Represents a recurring work schedule pattern that defines when and where a user works regularly.

A work plan recurrence allows a user to establish repeating weekly work schedules. The following list shows examples:

- Office work every Monday, Wednesday, and Friday from 9 AM to 5 PM
- Remote work on Tuesdays and Thursdays

A user can create multiple recurrences to accommodate different work patterns throughout the week. Time-off entries can't be set as recurring patterns and must be added as individual [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) objects.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-list-recurrences?view=graph-rest-1.0) | [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) collection | Get the [recurrences](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) from a user's work plan via the **recurrences** navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-post-recurrences?view=graph-rest-1.0) | [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) | Create a new [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) object in a user's work plan. |
| [Update](https://learn.microsoft.com/en-us/graph/api/workplanrecurrence-update?view=graph-rest-1.0) | [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) | Update the properties of a [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) object in a user's work plan. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/workplanrecurrence-delete?view=graph-rest-1.0) | None | Delete a [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) object from a user's work plan. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| end | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The end date and time for the recurring work plan. |
| id | String | Unique identifier for the recurrence. |
| placeId | String | Identifier of a place from the Microsoft Graph Places Directory API. Only applicable when **workLocationType** is set to `office`. |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The recurrence pattern that defines when this work plan repeats. |
| start | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The start date and time for the recurring work plan. |
| workLocationType | [workLocationType](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0#worklocationtype-values) | The type of work location. It can't be set to `timeOff`. Supports a subset of the values for **workLocationType**. The possible values are: `unspecified`, `office`, `remote`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "end": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "id": "String (identifier)",
  "placeId": "String",
  "recurrence": {"@odata.type": "microsoft.graph.patternedRecurrence"},
  "start": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "workLocationType": "String"
}
```
