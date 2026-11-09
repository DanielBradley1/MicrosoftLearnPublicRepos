<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequestupdateresponse -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# creditRequestUpdateResponse resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the result of the [batchRecordDecisions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/creditrequest-batchrecorddecisions) action, including summary counts and per-item results. The action isn't atomic; per-item results appear in the same order as the input items.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `failedCount` | Int32 | The number of items that returned a status other than `succeeded`. |
| `responses` | [creditRequestUpdateResponseItem](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/creditrequestupdateresponseitem) collection | The per-item results, in the same order as the items in the request. |
| `succeededCount` | Int32 | The number of items that were updated successfully. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.creditRequestUpdateResponse",
  "failedCount": "Int32",
  "responses": [
    {
      "@odata.type": "microsoft.graph.creditRequestUpdateResponseItem"
    }
  ],
  "succeededCount": "Int32"
}
```
