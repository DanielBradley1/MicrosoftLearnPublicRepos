<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# operationApprovalRequest resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The OperationApprovalRequest entity encompasses the operation an admin wishes to perform and is requesting approval to complete. It contains the detail of the operation one wishes to perform, user metadata of the requestor, and a justification for the change. It allows for several operations for both the requestor and the potential approver to either approve, deny, or cancel the request and a response justification to provide information for the decision.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List operationApprovalRequests](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-list?view=graph-rest-beta) | [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) collection | List properties and relationships of the [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) objects. |
| [Get operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-get?view=graph-rest-beta) | [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) | Read properties and relationships of the [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) object. |
| [Create operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-create?view=graph-rest-beta) | [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) | Create a new [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) object. |
| [Delete operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-delete?view=graph-rest-beta) | None | Deletes a [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta). |
| [Update operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-update?view=graph-rest-beta) | [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) | Update the properties of a [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) object. |
| [cancelMyRequest action](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-cancelmyrequest?view=graph-rest-beta) | None |  |
| [approve action](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-approve?view=graph-rest-beta) | String | Approves the requested instance of an operationApprovalRequest. |
| [reject action](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-reject?view=graph-rest-beta) | String | Rejects the requested instance of an operationApprovalRequest. |
| [cancelApproval action](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-cancelapproval?view=graph-rest-beta) | String | Cancels an already approved instance of an operationApprovalRequest. |
| [retrieveRequestStatus action](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-retrieverequeststatus?view=graph-rest-beta) | [operationApprovalRequestEntityStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequestentitystatus?view=graph-rest-beta) |  |
| [retrieveMyRequestById function](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-retrievemyrequestbyid?view=graph-rest-beta) | [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) |  |
| [retrieveMyRequests function](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalrequest-retrievemyrequests?view=graph-rest-beta) | [operationApprovalRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequest?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the request. This ID is assigned at when the request is created. Read-only. |
| requestDateTime | DateTimeOffset | Indicates the DateTime that the request was made. The value cannot be modified and is automatically populated when the request is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. Read-only. This property is read-only. |
| expirationDateTime | DateTimeOffset | Indicates the DateTime when any action on the approval request is no longer permitted. The value cannot be modified and is automatically populated when the request is created using expiration offset values defined in the service controllers. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. Read-only. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | Indicates the last DateTime that the request was modified. The value cannot be modified and is automatically populated whenever values in the request are updated. For example, when the 'status' property changes from `needsApproval` to `approved`. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. Read-only. This property is read-only. |
| requestor | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-identityset?view=graph-rest-beta) | The identity of the requestor as an Identity Set. Optionally contains the application ID, the device ID and the User ID. See information about this type here: [https://learn.microsoft.com/graph/api/resources/identityset?view=graph-rest-1.0](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0). Read-only. This property is read-only. |
| approver | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-identityset?view=graph-rest-beta) | The identity of the approver as an Identity Set. Optionally contains the application ID, the device ID and the User ID. See information about this type here: [https://learn.microsoft.com/graph/api/resources/identityset?view=graph-rest-1.0](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0). Read-only. This property is read-only. |
| status | [operationApprovalRequestStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalrequeststatus?view=graph-rest-beta) | The current approval status of the request. Possible values are: `unknown`, `needsApproval`, `approved`, `rejected`, `cancelled`, `completed`, `expired`. Default value is `unknown`. Read-only. This property is read-only. Possible values are: `unknown`, `needsApproval`, `approved`, `rejected`, `cancelled`, `completed`, `expired`, `unknownFutureValue`. |
| requestJustification | String | Indicates the justification for creating the request. Maximum length of justification is 1024 characters. For example: 'Needed for Feb 2023 application baseline updates.' Read-only. This property is read-only. |
| approvalJustification | String | Indicates the justification for approving or rejecting the request. Maximum length of justification is 1024 characters. For example: 'Approved per Change 23423 - needed for Feb 2023 application baseline updates.' Read-only. This property is read-only. |
| requiredOperationApprovalPolicyTypes | [operationApprovalPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicytype?view=graph-rest-beta) collection | Indicates the approval policy types required by the request in order for the request to be approved or rejected. Read-only. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.operationApprovalRequest",
  "id": "String (identifier)",
  "requestDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "requestor": {
    "@odata.type": "microsoft.graph.identitySet",
    "application": {
      "@odata.type": "microsoft.graph.identity",
      "id": "String",
      "displayName": "String"
    },
    "device": {
      "@odata.type": "microsoft.graph.identity",
      "id": "String",
      "displayName": "String"
    },
    "user": {
      "@odata.type": "microsoft.graph.identity",
      "id": "String",
      "displayName": "String"
    }
  },
  "approver": {
    "@odata.type": "microsoft.graph.identitySet",
    "application": {
      "@odata.type": "microsoft.graph.identity",
      "id": "String",
      "displayName": "String"
    },
    "device": {
      "@odata.type": "microsoft.graph.identity",
      "id": "String",
      "displayName": "String"
    },
    "user": {
      "@odata.type": "microsoft.graph.identity",
      "id": "String",
      "displayName": "String"
    }
  },
  "status": "String",
  "requestJustification": "String",
  "approvalJustification": "String",
  "requiredOperationApprovalPolicyTypes": [
    "String"
  ]
}
```
