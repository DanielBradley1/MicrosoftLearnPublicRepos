<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-29 -->

# timeOffRequest resource type

Namespace: microsoft.graph

Represents a type of shift request to take [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/timeoffrequest-list?view=graph-rest-1.0) | [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0) collection | Get the list of **timeOffRequest** objects in this schedule. |
| [Create](https://learn.microsoft.com/en-us/graph/api/timeoffrequest-post?view=graph-rest-1.0) | [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0) | Create a **timeOffRequest** objects in this schedule. |
| [Get](https://learn.microsoft.com/en-us/graph/api/timeoffrequest-get?view=graph-rest-1.0) | [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0) | Read the properties and relationships of a **timeOffRequest** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/timeoffrequest-delete?view=graph-rest-1.0) | None | Delete a **timeOffRequest** object. |
| [Approve](https://learn.microsoft.com/en-us/graph/api/timeoffrequest-approve?view=graph-rest-1.0) | None | Approve a time off request. |
| [Decline](https://learn.microsoft.com/en-us/graph/api/timeoffrequest-decline?view=graph-rest-1.0) | None | Decline a time off request. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | scheduleChangeRequestActor | Indicates who the request is assigned to. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0).The possible values are: `sender`, `recipient`, `manager`, `system`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the entity. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the entity was created. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| endDateTime | DateTimeOffset | The date and time the time off ends in ISO 8601 format and in UTC time. |
| id | String | The unique identifier for the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who last modified the entity. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the entity was last modified. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| managerActionDateTime | DateTimeOffset | The date and time when the manager approved or declined the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| managerActionMessage | String | The message sent by the manager regarding the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| managerUserId | String | The user ID of the manager who approved or declined the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderDateTime | DateTimeOffset | The date and time when the sender sent the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderMessage | String | The message sent by the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderUserId | String | The user ID of the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| startDateTime | DateTimeOffset | The date and time the time off starts in ISO 8601 format and in UTC time. |
| state | scheduleChangeState | The state of the entity. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0).The possible values are: `pending`, `approved`, `declined`, `unknownFutureValue`. |
| timeOffReasonId | String | The reason for the time off. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timeOffRequest",
  "id": "String (identifier)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "assignedTo": "String",
  "state": "String",
  "senderMessage": "String",
  "senderDateTime": "String (timestamp)",
  "managerActionMessage": "String",
  "managerActionDateTime": "String (timestamp)",
  "senderUserId": "String",
  "managerUserId": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "timeOffReasonId": "String"
}
```
