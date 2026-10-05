<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# workHoursAndLocationsSetting resource type

Namespace: microsoft.graph

Represents your working hours and location preferences for modern hybrid work scenarios.

Work hours and location information are useful in scenarios that involve planning in-office days with colleagues and scheduling meetings across different working hours and time zones. You can [get](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-get?view=graph-rest-1.0) and [update](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-update?view=graph-rest-1.0) your work hours and locations as part of your personal work planning. Use these APIs to set different work locations and schedules to accommodate your flexible work arrangements.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-get?view=graph-rest-1.0) | [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0) | Get the properties and relationships of your own [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-update?view=graph-rest-1.0) | [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0) | Update the properties of your own [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0). |
| [Occurrences view](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-occurrencesview?view=graph-rest-1.0) | [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) collection | Get [work plan occurrences](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) from your own work plan within a specified date range. |
| [List recurrences](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-list-recurrences?view=graph-rest-1.0) | [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) collection | Get the [recurrences](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) from your own work plan via the **recurrences** navigation property. |
| [Create recurrence](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-post-recurrences?view=graph-rest-1.0) | [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) | Create a new [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) object in your own work plan. |
| [Create occurrence](https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-post-occurrences?view=graph-rest-1.0) | [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) | Create a new [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) object in your own work plan. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maxSharedWorkLocationDetails | [maxWorkLocationDetails](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0#maxworklocationdetails-values) | Controls the level of work location details that can be shared with colleagues. The possible values are: `unknown`, `none`, `approximate`, `specific`, `unknownFutureValue`. |

### maxWorkLocationDetails values

| Member | Description |
| :--- | :--- |
| unknown | The level of location details to share is unknown. This value exists for backward compatibility only and can't be set as a new value. |
| none | No location details are shared. |
| approximate | Only general work location type is shared, such as office or remote. |
| specific | Detailed location information is shared, such as building and desk information. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| occurrences | [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) collection | Collection of work plan occurrences. |
| recurrences | [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) collection | Collection of recurring work plans defined by the user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "maxSharedWorkLocationDetails": "String"
}
```
