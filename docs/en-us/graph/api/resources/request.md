<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/request?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# request resource type

Namespace: microsoft.graph

Represents the details of a request in [PIM](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-1.0) or [user consent request](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) APIs.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalId | String | The identifier of the approval of the request. |
| completedDateTime | DateTimeOffset | The request completion date time. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The principal that created the request. |
| createdDateTime | DateTimeOffset | The request creation date time. |
| customData | String | Free text field to define any custom data for the request. Not used. |
| id | String | The unique identifier for the request object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| status | String | The status of the request. Not nullable. The possible values are: `Canceled`, `Denied`, `Failed`, `Granted`, `PendingAdminDecision`, `PendingApproval`, `PendingProvisioning`, `PendingScheduleCreation`, `Provisioned`, `Revoked`, and `ScheduleCreated`. Not nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.request",
  "id": "String (identifier)",
  "status": "String",
  "completedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "approvalId": "String",
  "customData": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```
