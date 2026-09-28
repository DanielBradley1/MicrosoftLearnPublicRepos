<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-29 -->

# offerShiftRequest resource type

Namespace: microsoft.graph

Represents a request to offer a shift to another user in the team.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/offershiftrequest-list?view=graph-rest-1.0) | Collection of [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0) | Read the properties and relationships of all **offerShiftRequest** objects in a team. |
| [Create](https://learn.microsoft.com/en-us/graph/api/offershiftrequest-post?view=graph-rest-1.0) | [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0) | Create an instance of an **offerShiftRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/offershiftrequest-get?view=graph-rest-1.0) | [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0) | Read the properties and relationships of an **offerShiftRequest** object. |
| [Approve](https://learn.microsoft.com/en-us/graph/api/offershiftrequest-approve?view=graph-rest-1.0) | None | Approve an **offerShiftRequest**. |
| [Decline](https://learn.microsoft.com/en-us/graph/api/offershiftrequest-decline?view=graph-rest-1.0) | None | Decline an **offerShiftRequest**. |

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
| recipientActionDateTime | DateTimeOffset | The date and time when the recipient approved or declined the request. |
| recipientActionMessage | String | The message sent by the recipient regarding the request. |
| recipientUserId | String | The recipient's user ID. |
| senderDateTime | DateTimeOffset | The date and time when the sender sent the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderMessage | String | The message sent by the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderShiftId | String | The sender's shift ID. |
| senderUserId | String | The user ID of the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| state | scheduleChangeState | The state of the entity. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0).The possible values are: `pending`, `approved`, `declined`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.offerShiftRequest",
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
  "recipientUserId": "String"
}
```
