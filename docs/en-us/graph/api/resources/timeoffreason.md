<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# timeOffReason resource type

Namespace: microsoft.graph

Represents a valid reason to take [time off](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/schedule-list-timeoffreasons?view=graph-rest-1.0) | [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) collection | Get the list of **timeOffReason** in a schedule. |
| [Create](https://learn.microsoft.com/en-us/graph/api/schedule-post-timeoffreasons?view=graph-rest-1.0) | [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) | Create a new **timeOffReason**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/timeoffreason-get?view=graph-rest-1.0) | [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) | Get a **timeOffReason** by ID. |
| [Replace](https://learn.microsoft.com/en-us/graph/api/timeoffreason-put?view=graph-rest-1.0) | [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) | Replace a **timeOffReason**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/timeoffreason-delete?view=graph-rest-1.0) | None | Mark a **timeOffReason** as inactive. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| code | String | The code of the **timeOffReason** to represent an external identifier. This field must be unique within the team in Microsoft Teams and uses an alphanumeric format, with a maximum of 100 characters. |
| createdDateTime | DateTimeOffset | The time stamp on which this **timeOffReason** was first created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The name of the **timeOffReason**. Required. |
| iconType | timeOffReasonIconType | Supported icon types are: `none`, `car`, `calendar,` `running`, `plane`, `firstAid`, `doctor`, `notWorking`, `clock`, `juryDuty`, `globe`, `cup`, `phone`, `weather`, `umbrella`, `piggyBank`, `dog`, `cake`, `trafficCone`, `pin`, `sunny`. Required. |
| id | String | Unique identifier for the time-off reason. |
| isActive | Boolean | Indicates whether the **timeOffReason** can be used when creating new entities or updating existing ones. Required. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that last updated this **timeOffReason**. |
| lastModifiedDateTime | DateTimeOffset | The time stamp on which this **timeOffReason** was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "iconType": "String",
  "id": "String (identifier)",
  "isActive": "Boolean",
  "lastModifiedBy": { "@odata.type":"microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)"
}
```
