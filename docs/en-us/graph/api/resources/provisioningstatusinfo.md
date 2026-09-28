<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisioningstatusinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# provisioningStatusInfo resource type

Namespace: microsoft.graph

Describes the status of the provisioning summary event. This object is configured in the **provisioningStatusInfo** property of [provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorInformation | [provisioningErrorInfo](https://learn.microsoft.com/en-us/graph/api/resources/provisioningerrorinfo?view=graph-rest-1.0) | If status isn't success/ skipped details for the error are contained in this. |
| status | provisioningResult | The possible values are: `success`, `warning`, `failure`, `skipped`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "status": "String",
  "errorInformation": {
    "@odata.type": "microsoft.graph.provisioningErrorInfo"
  }
}
```
