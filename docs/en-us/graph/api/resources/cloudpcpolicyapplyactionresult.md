<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpolicyapplyactionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-11 -->

# cloudPcPolicyApplyActionResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the policy apply status, apply start time, and finish time. `Frontline shared` only.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | string | The status of the applied operation. The possible values are: `succeeded`, `pending`,`failed`, and `unknownFutureValue`. |
| startDateTime | DateTime | The date and time when the operation was applied. |
| finishDateTime | DateTime | The date and time when the operation finished. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "https://graph.microsoft.com/beta/$metadata#cloudPcPolicyApplyActionResult",
  "status": "succeeded",
  "startDateTime": "2024-10-10T00:00:00",
  "finishDateTime": "2024-10-11T00:00:00"
}
```
