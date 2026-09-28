<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-23 -->

# timeCard resource type

Namespace: microsoft.graph

Represents a timecard entry in the schedule.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/schedule-list-timecards?view=graph-rest-1.0) | [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) collection | Get a list of the **timeCard** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/schedule-post-timecards?view=graph-rest-1.0) | [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) | Create a new **timeCard** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/timecard-get?view=graph-rest-1.0) | [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) | Read the properties and relationships of a **timeCard** object. |
| [Replace](https://learn.microsoft.com/en-us/graph/api/timecard-replace?view=graph-rest-1.0) | [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) | Replace a **timeCard** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/schedule-delete-timecards?view=graph-rest-1.0) | None | Delete a timeCard object. |
| [Clock in](https://learn.microsoft.com/en-us/graph/api/timecard-clockin?view=graph-rest-1.0) | [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) | Clock in to start a **timeCard**. |
| [Clock out](https://learn.microsoft.com/en-us/graph/api/timecard-clockout?view=graph-rest-1.0) | None | Clock out to end an open **timeCard**. |
| [Start break](https://learn.microsoft.com/en-us/graph/api/timecard-startbreak?view=graph-rest-1.0) | None | Start a **timeCardBreak** in a specific **timeCard**. |
| [End break](https://learn.microsoft.com/en-us/graph/api/timecard-endbreak?view=graph-rest-1.0) | None | End the open **timeCardBreak** in a specific **timeCard**. |
| [Confirm](https://learn.microsoft.com/en-us/graph/api/timecard-confirm?view=graph-rest-1.0) | None | Confirm a **timeCard** record. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| breaks | [timeCardBreak](https://learn.microsoft.com/en-us/graph/api/resources/timecardbreak?view=graph-rest-1.0) collection | The list of breaks associated with the **timeCard**. |
| clockInEvent | [timeCardEvent](https://learn.microsoft.com/en-us/graph/api/resources/timecardevent?view=graph-rest-1.0) | The clock-in event of the **timeCard**. |
| clockOutEvent | [timeCardEvent](https://learn.microsoft.com/en-us/graph/api/resources/timecardevent?view=graph-rest-1.0) | The clock-out event of the **timeCard**. |
| confirmedBy | confirmedBy | Indicates whether this **timeCard** entry is confirmed. The possible values are: `none`, `user`, `manager`, `unknownFutureValue`. |
| createdBy | [IdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of this **timecard**. |
| createdDateTime | DateTimeOffset | The date and time at which the **timeCard** was created. |
| id | String | Unique identifier for the **timeCard**. |
| lastModifiedBy | [IdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the last modifier of this **timecard**. |
| lastModifiedDateTime | DateTimeOffset | The timestamp in which the **timeCard** was last modified. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Notes about the **timeCard**. |
| originalEntry | [timeCardEntry](https://learn.microsoft.com/en-us/graph/api/resources/timecardentry?view=graph-rest-1.0) | The original **timeCardEntry** of the **timeCard** before it was edited. |
| state | timeCardState | The current state of the **timeCard** during its life cycle. The possible values are: `clockedIn`, `onBreak`, `clockedOut`, `unknownFutureValue`. |
| userId | String | User ID to which the **timeCard** belongs. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timeCard",
  "id": "String (identifier)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "userId": "String",
  "state": "String",
  "clockInEvent": {
    "@odata.type": "microsoft.graph.timeCardEvent"
  },
  "clockOutEvent": {
    "@odata.type": "microsoft.graph.timeCardEvent"
  },
  "breaks": [
    {
      "@odata.type": "microsoft.graph.timeCardBreak"
    }
  ],
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "originalEntry": {
    "@odata.type": "microsoft.graph.timeCardEntry"
  },
  "confirmedBy": "String"
}
```
