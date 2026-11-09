<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequestupdateitem -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# creditRequestUpdateItem resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a single decision in the request body of the [batchRecordDecisions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-batchrecorddecisions) action. Each item targets one [creditRequest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest) by `requestId`, sets a target `state`, and supplies an `etag` for optimistic concurrency.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `etag` | String | The concurrency token from the latest read of the credit request. Must be one quoted strong ETag, such as `"\"7f94e342\""`. Weak ETags and `*` are malformed. A missing, `null`, malformed, or stale value returns a per-item `preconditionFailed` result. |
| `requestId` | String | The `id` of the credit request to update. A missing or `null` value returns a per-item `failed` result. Values must be unique within the payload; duplicates fail the whole request. |
| `state` | [creditRequestState](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequest#creditrequeststate-enumeration) | The target state. Use `approved` or `rejected`. A missing value or an unsupported transition returns a per-item `invalidStateTransition` result. An explicit JSON `null` fails the whole request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.creditRequestUpdateItem",
  "etag": "String",
  "requestId": "String",
  "state": "String"
}
```
