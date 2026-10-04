<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# workPlanOccurrence resource type

Namespace: microsoft.graph

Represents a specific work schedule instance for a particular day or time period in a user's work plan.

Work plan occurrences can be automatically generated from a user's recurring work patterns or manually created for special arrangements. These occurrences are useful for handling exceptions to the user's regular schedules. The following list shows examples:

- Working different hours for a specific day
- Working from a different location
- Taking time off

When a work plan occurrence exists for the same time period as a recurring pattern, the occurrence takes precedence, allowing for flexible schedule adjustments.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-post-occurrences?view=graph-rest-1.0) | [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) | Create a new [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) object in a user's work plan. |
| [Update](https://learn.microsoft.com/en-us/graph/api/workplanoccurrence-update?view=graph-rest-1.0) | [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) | Update the properties of a [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) object in a user's work plan. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/workplanoccurrence-delete?view=graph-rest-1.0) | None | Delete a [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) object from a user's work plan. |
| [Set current location](https://learn.microsoft.com/en-us/graph/api/workplanoccurrence-setcurrentlocation?view=graph-rest-1.0) | None | Update a user's [work](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) location for the current day or current active segment. |
| [Occurrences view](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-occurrencesview?view=graph-rest-1.0) | [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) collection | Get [work plan occurrences](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) from a user's work plan within a specified date range. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| end | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The end date and time for this occurrence. |
| id | String | Unique identifier for the occurrence. |
| placeId | String | Identifier of a place from the Microsoft Graph Places Directory API. Only applicable when **workLocationType** is set to `office`. |
| recurrenceId | String | The identifier of the parent recurrence pattern that generated this occurrence. The value is `null` for time-off occurrences because they don't have a parent recurrence. |
| start | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The start date and time for this occurrence. |
| timeOffDetails | [timeOffDetails](https://learn.microsoft.com/en-us/graph/api/resources/timeoffdetails?view=graph-rest-1.0) | The details about the time off. Only applicable when **workLocationType** is set to `timeOff`. |
| workLocationType | [workLocationType](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0#worklocationtype-values) | The type of work location. The possible values are: `unspecified`, `office`, `remote`, `timeOff`, `unknownFutureValue`. |

### workLocationType values

| Member | Description |
| :--- | :--- |
| unspecified | Indicates that the user didn't specify the location. |
| office | Indicates that the user works from an office location. |
| remote | Indicates that the user works remotely. |
| timeOff | Indicates that the user is on time-off. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "end": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "id": "String (identifier)",
  "placeId": "String",
  "recurrenceId": "String",
  "start": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "timeOffDetails": {"@odata.type": "microsoft.graph.timeOffDetails"},
  "workLocationType": "String"
}
```
