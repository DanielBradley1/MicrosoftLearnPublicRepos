<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-29 -->

# scheduleChangeRequest resource type

Namespace: microsoft.graph

An abstract type that represents a schedule change request.

Base type of [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0), [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0), and [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0).

Inherits from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | scheduleChangeRequestActor | Indicates who the request is assigned to. The possible values are: `sender`, `recipient`, `manager`, `system`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the **scheduleChangeRequest**. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the **scheduleChangeRequest** was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on `Jan 1, 2014 is 2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| id | String | The unique identifier for the **scheduleChangeRequest**. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who last modified the **scheduleChangeRequest**. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the **scheduleChangeRequest** was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on `Jan 1, 2014 is 2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| managerActionDateTime | DateTimeOffset | The date and time when the manager approved or declined the **scheduleChangeRequest**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on `Jan 1, 2014 is 2014-01-01T00:00:00Z`. |
| managerActionMessage | String | The message sent by the manager regarding the **scheduleChangeRequest**. Optional. |
| managerUserId | String | The user ID of the manager who approved or declined the **scheduleChangeRequest**. |
| senderDateTime | DateTimeOffset | The date and time when the sender sent the **scheduleChangeRequest**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on `Jan 1, 2014 is 2014-01-01T00:00:00Z`. |
| senderMessage | String | The message sent by the sender of the **scheduleChangeRequest**. Optional. |
| senderUserId | String | The user ID of the sender of the **scheduleChangeRequest**. |
| state | scheduleChangeState | The state of the **scheduleChangeRequest**. The possible values are: `pending`, `approved`, `declined`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.scheduleChangeRequest",
  "assignedTo": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "managerActionDateTime": "String (timestamp)",
  "managerActionMessage": "String",
  "managerUserId": "String",
  "senderDateTime": "String (timestamp)",
  "senderMessage": "String",
  "senderUserId": "String",
  "state": "String"
}
```
