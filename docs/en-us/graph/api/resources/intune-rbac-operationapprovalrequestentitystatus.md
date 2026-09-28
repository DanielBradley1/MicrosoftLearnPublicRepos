<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequestentitystatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# operationApprovalRequestEntityStatus resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The operationApprovalRequestEntityStatus complex type is used to provide the basic infortmation relating to the status of a request without revealing too much information to the calling user as it may be an object out of scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| requestId | String | The unique identifier of the OperationApprovalRequest. This property cannot be modified and is required when the entity status is created. Read-only. This property is read-only. |
| requestExpirationDateTime | DateTimeOffset | Indicates the DateTime when any action on the OperationApprovalRequest is no longer permitted. The value cannot be modified and is automatically populated when the request is created using expiration offset values defined in the service controllers. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. Read-only. This property is read-only. |
| requestStatus | [operationApprovalRequestStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequeststatus?view=graph-rest-beta) | The current approval status of the OperationApprovalRequest. Possible values are: `unknown`, `needsApproval`, `approved`, `rejected`, `cancelled`, `completed`, `expired`. Default value is `unknown`. Read-only. This property is read-only. Possible values are: `unknown`, `needsApproval`, `approved`, `rejected`, `cancelled`, `completed`, `expired`, `unknownFutureValue`. |
| entityLocked | Boolean | The status of the Entity connected to the OperationApprovalRequest in regard to changes, whether further requests are allowed or if the Entity is locked. When `true`, a lock is present on the Entity and no approval requests can be currently made for it. When `false`, the Entity is not locked and approval requests are allowed. Default value is `false`. Read-only. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.operationApprovalRequestEntityStatus",
  "requestId": "String",
  "requestExpirationDateTime": "String (timestamp)",
  "requestStatus": "String",
  "entityLocked": true
}
```
