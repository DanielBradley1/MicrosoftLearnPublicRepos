<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-29 -->

# swapShiftsChangeRequest resource type

Namespace: microsoft.graph

Represents a type of shift request to swap a [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) with another user in the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/swapshiftschangerequest-list?view=graph-rest-1.0) | Collection of [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0) | List the properties and relationships of **swapShiftsChangeRequest** objects in a team. |
| [Create](https://learn.microsoft.com/en-us/graph/api/swapshiftschangerequest-post?view=graph-rest-1.0) | [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0) | Create an instance of a **swapShiftsChangeRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/swapshiftschangerequest-get?view=graph-rest-1.0) | [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0) | Read the properties and relationships of a **swapShiftsChangeRequest** object. |
| [Approve](https://learn.microsoft.com/en-us/graph/api/swapshiftschangerequest-approve?view=graph-rest-1.0) | None | Approve a **swapShiftsChangeRequest**. |
| [Decline](https://learn.microsoft.com/en-us/graph/api/swapshiftschangerequest-decline?view=graph-rest-1.0) | None | Decline a **swapShiftsChangeRequest**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | scheduleChangeRequestActor | Indicates who the request is assigned to. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0).The possible values are: `sender`, `recipient`, `manager`, `system`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the entity. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the entity was created. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| id | String | The unique identifier for the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who last modified the entity. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the entity was last modified. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| managerActionDateTime | DateTimeOffset | The date and time when the manager approved or declined the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| managerActionMessage | String | The message sent by the manager regarding the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| managerUserId | String | The user ID of the manager who approved or declined the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| recipientActionDateTime | DateTimeOffset | The date and time when the recipient approved or declined the request. Inherited from [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0). |
| recipientActionMessage | String | The message sent by the recipient regarding the request. Inherited from [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0). |
| recipientShiftId | String | The recipient's Shift ID |
| recipientUserId | String | The recipient's user ID. Inherited from [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0). |
| senderDateTime | DateTimeOffset | The date and time when the sender sent the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderMessage | String | The message sent by the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderShiftId | String | The sender's shift ID. Inherited from [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0). |
| senderUserId | String | The user ID of the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| state | scheduleChangeState | The state of the entity. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0).The possible values are: `pending`, `approved`, `declined`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.swapShiftsChangeRequest",
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
  "recipientActionMessage": "String",
  "recipientActionDateTime": "String (timestamp)",
  "senderShiftId": "String",
  "recipientUserId": "String",
  "recipientShiftId": "String"
}
```
