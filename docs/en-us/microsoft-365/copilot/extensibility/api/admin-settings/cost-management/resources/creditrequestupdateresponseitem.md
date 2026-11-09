<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequestupdateresponseitem -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# creditRequestUpdateResponseItem resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the result for a single item in the [batchRecordDecisions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-batchrecorddecisions) action. Returned in the `responses` collection of a [creditRequestUpdateResponse](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequestupdateresponse).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `etag` | String | The updated concurrency token. Present only when `status` is `succeeded`. |
| `message` | String | A human-readable error message. Present for failed items when more detail is available. |
| `requestId` | String | The identifier of the targeted credit request. If the input item omitted `requestId`, the value is the all-zero GUID \(`00000000-0000-0000-0000-000000000000`\). |
| `status` | [creditRequestUpdateStatus](#creditrequestupdatestatus-enumeration) | The processing status for the item. |

### creditRequestUpdateStatus enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value | Description |
| :--- | :--- |
| `succeeded` | The update was applied. |
| `notFound` | The credit request doesn't exist or doesn't belong to the tenant. |
| `preconditionFailed` | The ETag is missing or malformed, or it doesn't match the current resource. Read the request again and retry with the current ETag. |
| `invalidStateTransition` | The state is missing, or the requested transition isn't supported for the current state. |
| `failed` | A missing `requestId`, a provider failure, or an unexpected error prevented the update. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.creditRequestUpdateResponseItem",
  "etag": "String",
  "message": "String",
  "requestId": "String",
  "status": "String"
}
```
