<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-29 -->

# openShiftChangeRequest resource type

Namespace: microsoft.graph

Represents request to claim an [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/openshiftchangerequest-list?view=graph-rest-1.0) | Collection of [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0) | List the properties and relationships of **openShiftChangeRequest** objects in a team. |
| [Create](https://learn.microsoft.com/en-us/graph/api/openshiftchangerequest-post?view=graph-rest-1.0) | [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0) | Create an instance of an **openShiftChangeRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/openshiftchangerequest-get?view=graph-rest-1.0) | [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0) | Read the properties and relationships of an **openShiftChangeRequest** object. |
| [Approve](https://learn.microsoft.com/en-us/graph/api/openshiftchangerequest-approve?view=graph-rest-1.0) | None | Approve an open shift change request. |
| [Decline](https://learn.microsoft.com/en-us/graph/api/openshiftchangerequest-decline?view=graph-rest-1.0) | None | Decline an open shift change request. |

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
| openShiftId | String | ID for the open shift. |
| senderDateTime | DateTimeOffset | The date and time when the sender sent the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderMessage | String | The message sent by the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| senderUserId | String | The user ID of the sender of the request. Inherited from [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0). |
| state | scheduleChangeState | The state of the **scheduleChangeRequest**. The possible values are: `pending`, `approved`, `declined`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.openShiftChangeRequest",
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
  "openShiftId": "String"
}
```
