<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# timeOff resource type

Namespace: microsoft.graph

Represents a unit of nonwork in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

Inherits from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/schedule-list-timesoff?view=graph-rest-1.0) | [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) collection | Get the list of **timeOff** objects in this schedule. |
| [Create](https://learn.microsoft.com/en-us/graph/api/schedule-post-timesoff?view=graph-rest-1.0) | [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) | Create a new **timeOff** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/timeoff-get?view=graph-rest-1.0) | [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) | Get a **timeOff** object by ID. |
| [Replace](https://learn.microsoft.com/en-us/graph/api/timeoff-put?view=graph-rest-1.0) | [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) | Replace a **timeOff** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/timeoff-delete?view=graph-rest-1.0) | None | Delete a **timeOff** object from the schedule. |
| [Stage for deletion](https://learn.microsoft.com/en-us/graph/api/changetrackedentity-stagefordeletion?view=graph-rest-1.0) | None | Stage the deletion of a [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) in draft mode. |

## Properties

| Name | Type | Description |
| --- | --- | --- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | ShiftsCreatedByDescription |
| createdDateTime | DateTimeOffset | The date and time at which this **timeOff** was first created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| draftTimeOff | [timeOffItem](https://learn.microsoft.com/en-us/graph/api/resources/timeoffitem?view=graph-rest-1.0) | The draft version of this **timeOff** item that is viewable by managers. It must be shared before it's visible to team members. Required. |
| id | String | ID of the **timeOff**. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| isStagedForDeletion | Boolean | The **timeOff** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that last updated this **timeOff**. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time at which this **timeOff** was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| sharedTimeOff | [timeOffItem](https://learn.microsoft.com/en-us/graph/api/resources/timeoffitem?view=graph-rest-1.0) | The shared version of this **timeOff** that is viewable by both employees and managers. Updates to the **sharedTimeOff** property send notifications to users in the Teams client. Required. |
| userId | String | ID of the user assigned to the **timeOff**. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timeOff",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "draftTimeOff": {"@odata.type": "microsoft.graph.timeOffItem"},
  "id": "String (identifier)",
  "isStagedForDeletion": "Boolean",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "sharedTimeOff": {"@odata.type": "microsoft.graph.timeOffItem"},
  "userId": "String"
}
```
